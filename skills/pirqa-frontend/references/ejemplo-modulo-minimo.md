# Ejemplo: módulo mínimo completo

Módulo `products` con lista, filtros en URL, estados (carga, error, vacío y sin
resultados) y un test de página. Es ilustrativo: adapta imports y componentes al
proyecto. El código suma menos de 120 líneas.

## 1. Contrato y hook de datos

```ts
// data/products.ts
export interface Product { id: string; name: string; status: 'active' | 'draft' }
export interface ProductQuery { q?: string; status?: Product['status'] }

// Contrato + punto de composición — datos-y-mutaciones.md
export const productRepository = {
  async list(_query: ProductQuery): Promise<Product[]> { return [] },
}
```

```ts
// features/products/use-products.ts
import { keepPreviousData, useQuery } from '@tanstack/react-query'
import { productRepository } from '@/data'

export const STATUS_FILTERS = ['all', 'active', 'draft'] as const
export type StatusFilter = (typeof STATUS_FILTERS)[number]
export interface ProductFilters { q: string; status: StatusFilter }

export function parseFilters(params: URLSearchParams): ProductFilters {
  const status = params.get('status')
  return {
    q: params.get('q')?.trim() ?? '',
    status: STATUS_FILTERS.includes(status as StatusFilter) ? (status as StatusFilter) : 'all',
  }
}

export function useProducts(filters: ProductFilters) {
  // QueryKey jerárquica — datos-y-mutaciones.md
  return useQuery({
    queryKey: ['products', 'list', filters],
    queryFn: () => productRepository.list({
      q: filters.q || undefined,
      status: filters.status === 'all' ? undefined : filters.status,
    }),
    placeholderData: keepPreviousData,
  })
}
```

## 2. Página

```tsx
// features/products/products-page.tsx
import { useSearchParams } from 'react-router-dom'
import { EmptyState, ErrorState } from '@/components/shared'
import { Skeleton } from '@/components/ui/skeleton'
import { parseFilters, STATUS_FILTERS, useProducts, type StatusFilter } from './use-products'

export function ProductsPage() {
  const [params, setParams] = useSearchParams()
  const filters = parseFilters(params)
  const query = useProducts(filters)
  const hasFilters = Boolean(filters.q || filters.status !== 'all')

  // Filtros en URL — patrones-de-pantalla.md §2
  const update = (patch: Partial<typeof filters>) => {
    const next = new URLSearchParams(params)
    if (patch.q !== undefined) patch.q ? next.set('q', patch.q) : next.delete('q')
    if (patch.status !== undefined) patch.status === 'all' ? next.delete('status') : next.set('status', patch.status)
    setParams(next, { replace: true })
  }

  // Estados: error con reintento — componentes.md
  if (query.isError) return <ErrorState onRetry={() => void query.refetch()} />
  if (query.isPending) return <Skeleton rows={5} />
  const items = query.data ?? []

  // Vacío inicial ≠ sin resultados — patrones-de-pantalla.md §1
  if (items.length === 0) {
    return hasFilters
      ? <EmptyState title="Sin resultados" action={<button onClick={() => setParams({}, { replace: true })}>Limpiar filtros</button>} />
      : <EmptyState title="Aún no hay productos" />
  }

  return (
    <section>
      <h1>Productos</h1>
      {/* Label accesible — accesibilidad.md */}
      <input aria-label="Buscar productos" value={filters.q}
        onChange={(e) => update({ q: e.target.value })} />
      <select aria-label="Estado" value={filters.status}
        onChange={(e) => update({ status: e.target.value as StatusFilter })}>
        {STATUS_FILTERS.map((s) => <option key={s} value={s}>{s}</option>)}
      </select>
      <ul>
        {items.map((p) => <li key={p.id}>{p.name} · {p.status}</li>)}
      </ul>
    </section>
  )
}
```

## 3. Test de página

```tsx
// features/products/products-page.test.tsx
import { render, screen } from '@testing-library/react'
import { MemoryRouter } from 'react-router-dom'
import { beforeEach, expect, it, vi } from 'vitest'
import { Providers } from '@/app/providers'
import { productRepository } from '@/data'
import { ProductsPage } from './products-page'

vi.mock('@/data', () => ({ productRepository: { list: vi.fn() } }))
beforeEach(() => vi.mocked(productRepository.list).mockReset())

// Test de página: vacío y sin resultados — testing.md
const renderAt = (url: string) => render(
  <Providers><MemoryRouter initialEntries={[url]}><ProductsPage /></MemoryRouter></Providers>,
)

it('distingue vacío inicial de filtros sin resultados', async () => {
  vi.mocked(productRepository.list).mockResolvedValue([])
  const { unmount } = renderAt('/products')
  expect(await screen.findByText('Aún no hay productos')).toBeInTheDocument()
  unmount()
  renderAt('/products?q=erp')
  expect(await screen.findByText('Sin resultados')).toBeInTheDocument()
})
```

En un módulo real añade: debounce si hay búsqueda de texto (default 300 ms),
paginación con el techo del repositorio, permisos y E2E con el adaptador mock
determinista del proyecto.
