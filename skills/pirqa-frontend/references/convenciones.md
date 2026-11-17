# Convenciones TypeScript, React y dominio (genérico)

Adáptalas al stack y a las reglas del proyecto. Si el repo ya define
convenciones, ganan las del repo.

## TypeScript

- Modo estricto: sin `any`; usa tipos de dominio, uniones discriminadas y
  `unknown` en bordes.
- Importa tipos con `import type` cuando el proyecto lo requiera.
- Maneja `undefined` al indexar arrays/records; no uses `!` para silenciar.
- Alias de rutas del proyecto; evita relativos largos entre capas.
- Export nombrado; `default` solo para lazy loading cuando aplique.
- Tipos explícitos en props y retornos públicos; infiere lo trivial.
- Formato con el formatter del proyecto (Prettier o equivalente); no mezcles.
- Lint con las reglas del proyecto; no las desactives sin motivo.

## React (o framework equivalente)

- Componentes como funciones nombradas, archivo `kebab-case`, componente
  `PascalCase`.
- Páginas con carga diferida y fallback.
- Hooks propios con prefijo `use` y archivo `use-*.ts`.
- Un hook de datos por archivo; queryKey estable y jerárquica.
- Filtros compartibles en la URL, no en estado local.
- Estado local solo para UI efímera (input antes de debounce, popover,
  selección temporal).
- No dupliques estado derivable: deriva en render o en una función pura.
- `useMemo`/`memo` solo con medición.
- No añadas comentarios que repitan el código; documenta decisiones no obvias.

## Nombres

| Elemento | Convención |
| --- | --- |
| Archivos | `kebab-case.ts` / `.tsx` |
| Componentes | `PascalCase` |
| Hooks | `useCamelCase` |
| Tipos/interfaces | `PascalCase` |
| Constantes | `SCREAMING_SNAKE_CASE` |
| QueryKeys | `['módulo', 'tipo', params]` |
| Claves de storage | `<producto>:<ámbito>` |

## Dominio y formatos

- **Dinero en la unidad mínima entera** (céntimos) y formateo con las utilidades
  del proyecto. Nunca dividas a mano ni uses `toFixed` para moneda.
- **Fechas** con las utilidades del proyecto y una fecha de referencia explícita
  para datos de demo. Parsea fechas sin hora a mediodía UTC para evitar
  corrimientos.
- **Números** con `Intl.NumberFormat` del locale del producto.
- **Etiquetas de dominio** en el archivo de labels del proyecto: estados,
  prioridades, categorías, roles, acciones. Nada de texto hardcodeado en
  componentes.
- **Identificadores:** los asigna el repositorio, no la vista.

## Persistencia local

- Claves namespaced (`<producto>:theme`, `<producto>:nav-collapsed`).
- Lee con `try/catch` y fallback en memoria.
- Nunca guardes datos de negocio en `localStorage`; usa el repositorio.

## Estructura de un módulo

```text
features/<módulo>/
├── <módulo>-page.tsx
├── <módulo>-detail-page.tsx        (si aplica)
├── <módulo>-form.tsx / schema.ts   (si aplica)
├── components/
├── hooks/
└── export/                         (si aplica)
```

Contratos en `data/contracts`, adaptadores en `data/mock|http`, registro en el
punto de composición, reglas puras en `domain/services`.
