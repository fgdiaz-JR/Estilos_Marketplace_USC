# Reglas y Directrices de Diseño - Versand / USC Marketplace

Estas directrices son de cumplimiento obligatorio para cualquier asistente o desarrollador que cree o modifique interfaces para el Marketplace USC.

---

## 1. Cero Colores Mágicos Arbitrarios (Strict Token Rule)
- **Prohibido**: Utilizar códigos hexadecimales o colores RGB sueltos en estilos en línea (`style="background: #5a2e99"` o `color: #333`).
- **Obligatorio**: Utilizar siempre los tokens de CSS variables definidos en `:root` y adaptados para modo oscuro:
  - Primarios: `var(--brand)`, `var(--brand-dark)`, `var(--brand-soft)`
  - Fondos / Superficies: `var(--surface)`, `var(--canvas)`
  - Textos: `var(--ink)`, `var(--muted)`
  - Bordes y líneas: `var(--line)`
  - Estados: `var(--success)`, `var(--warning)`, `var(--danger)` y sus variantes `-soft`.

## 2. Coherencia Estructural de Layout
- Toda vista autenticada debe basarse en el patrón `.shell` (con `.sidebar`, `.main`, `.topbar`, `.content`).
- Toda vista de autenticación o onboarding debe seguir el patrón split de `.login` (`.login-visual` y `.login-panel`).
- Conservar los anchos responsivos y márgenes de contenedor:
  - En `.content`: `width: min(1380px, 91%)`, centrado con margen automático.
  - En encabezados de página: `.page-head` con `.eyebrow`, `h1` y `.lead`.

## 3. Responsive Breakpoints Nativos
El CSS ya incluye los siguientes puntos de quiebre. No se deben romper ni sobreescribir:
- **`max-width: 1050px`**: Las grillas `.kpi-grid` colapsan a 2 columnas. Los grids de dos columnas (`.dashboard-grid`, `.buyer-layout`) colapsan a 1 sola columna.
- **`max-width: 730px` / `700px`**:
  - En móviles, `.sidebar` se oculta (`display: none`).
  - `.shell` se transforma en bloque directo.
  - En la vista de login, se activa el botón `.mobile-login-toggle`.
  - Las filas de pedidos `.order-row` pasan a formato tarjeta apilada.

## 4. Soporte para Modo Oscuro (`data-theme="dark"`)
- Nunca utilices estilos que asuman que el fondo siempre es blanco.
- Usa `var(--surface)` para fondos de tarjetas y `var(--ink)` para textos.
- Para habilitar el cambio de tema, siempre incluye el botón:
  ```html
  <button id="themeToggle" class="icon-btn" aria-label="Cambiar tema">☾</button>
  ```
  E inicialízalo en JS llamando a `setupTheme()` de `versand-auth.js`.

## 5. Logotipo Oficial e Identidad Visual
- El logo oficial está contenido como string SVG en la variable `logo` dentro de `scripts/versand-auth.js`.
- Se debe inyectar siempre dentro de elementos con la clase `.brand-mark`:
  ```javascript
  document.querySelector("#logo").innerHTML = logo;
  ```
- Nunca sustituyas el logo por iconos o imágenes externas sin aprobación de diseño de la USC.

## 6. Formularios y Estados de Validación
- Todo input debe envolverse dentro de un `<label class="field">`.
- En caso de errores o mensajes de éxito dinámicos, usa las clases:
  - `.field-error-msg` para advertencias o errores en rojo (`var(--danger)`).
  - `.field-success-msg` para confirmaciones en verde (`var(--success)`).
- Los botones de envío en formularios de ancho completo deben llevar la clase `.login-submit` o estilo `width: 100%`.

