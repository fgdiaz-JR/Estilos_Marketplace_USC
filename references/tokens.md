# Design Tokens - Versand / USC Marketplace

Este documento define la totalidad de tokens visuales y variables CSS oficiales para cualquier módulo del Marketplace de la Universidad Santiago de Cali (USC).

---

## 1. Paleta de Colores y Estados

### Modo Claro (`:root`)
| Token | Valor Hex | Uso / Descripción |
| :--- | :--- | :--- |
| `--brand` | `#7046c8` | Color de marca primario (morado principal), botones primarios, acentos activos |
| `--brand-dark` | `#4c2993` | Hover de botones primarios y variantes oscuras |
| `--brand-soft` | `#eee7ff` | Fondos de acento suave, banners informativos, highlights |
| `--violet` | `#a074ee` | Color secundario / violeta de apoyo, barras secundarias de gráficos |
| `--canvas` | `#f7f5fb` | Fondo general de la página / aplicación |
| `--surface` | `#ffffff` | Fondo de tarjetas, paneles, inputs y modales |
| `--ink` | `#211b35` | Color de texto principal (títulos, encabezados, contenido destacado) |
| `--muted` | `#786f8f` | Texto secundario, subtítulos, etiquetas y placeholders |
| `--line` | `#e6e0f0` | Bordes de tarjetas, divisores de tablas, separadores |
| `--success` | `#247c63` | Estado exitoso, pedidos entregados, tendencias positivas |
| `--success-soft` | `#e2f6ee` | Fondo de badges y alertas de éxito |
| `--warning` | `#a2660a` | Estado pendiente / alerta, pedidos en tránsito, pins de mapa |
| `--warning-soft` | `#fff2d9` | Fondo de badges y alertas de advertencia |
| `--danger` | `#b84b63` | Estado de error / incidencia crítica, tendencias negativas |
| `--danger-soft` | `#ffe8ed` | Fondo de badges y alertas de error |

### Modo Oscuro (`[data-theme="dark"]`)
| Token | Valor Hex | Adaptación |
| :--- | :--- | :--- |
| `--brand` | `#b18aff` | Morado claro con alto contraste |
| `--brand-dark` | `#e2d5ff` | Tono pastel para hover e interacciones |
| `--brand-soft` | `#2b1d48` | Fondo profundo para destacar elementos |
| `--violet` | `#8c67dd` | Violeta atenuado |
| `--canvas` | `#0e0a18` | Fondo oscuro profundo |
| `--surface` | `#19132a` | Superficie de tarjetas y paneles oscuros |
| `--ink` | `#f5f1ff` | Texto claro de alta legibilidad |
| `--muted` | `#afa5c5` | Texto secundario atenuado |
| `--line` | `#382e50` | Bordes sutiles oscuros |
| `--success` | `#72dfb3` | Verde menta brillante |
| `--success-soft` | `#173d34` | Fondo de éxito oscuro |
| `--warning` | `#ffd06e` | Ámbar cálido |
| `--warning-soft` | `#473619` | Fondo de advertencia oscuro |
| `--danger` | `#ff91a7` | Rosa / rojo suave |
| `--danger-soft` | `#4d2633` | Fondo de peligro oscuro |

---

## 2. Tipografía

- **Familia principal**:
  ```css
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", sans-serif;
  ```
- **Escala y Pesos**:
  - Títulos principales `h1`: `clamp(30px, 4vw, 46px)`, peso `850`, letter-spacing `-0.055em`, line-height `1.05`.
  - Títulos de sección `h2`: `22px` (o `17px` en paneles), letter-spacing `-0.035em`.
  - Sobretítulos `.eyebrow`: `10px`, peso `850`, mayúsculas, letter-spacing `0.13em`, color `var(--brand)`.
  - Subtítulos / secundarios `.muted`, `.lead`: `13px`, color `var(--muted)`.
  - Texto de botones `.btn`: peso `780`.
  - Valores KPI `.kpi-value`: `29px`, peso `850`, letter-spacing `-0.05em`.
  - Badges `.badge`: `10px`, peso `850`.

---

## 3. Sombras, Bordes y Transiciones

- **Sombra estándar (`--shadow`)**:
  - Modo claro: `0 16px 42px rgba(57, 32, 107, 0.1)`
  - Modo oscuro: `0 18px 46px rgba(0, 0, 0, 0.3)`
- **Radio de bordes**:
  - Tarjetas (`.card`): `15px`
  - Paneles (`.panel`): `15px`
  - Botones (`.btn`): `10px`
  - Inputs (`.field input`): `10px`
  - Badges (`.badge`): `99px` (completamente redondeado)
  - Modales (`.modal`): `15px`
  - Brand Mark (`.brand-mark`): `13px`
- **Transición global**:
  - `transition: .25s` para cambio fluido entre temas claro y oscuro.

