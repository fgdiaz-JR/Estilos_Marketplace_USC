---
name: marketplace-usc-styles
description: >-
  Design system, UI guidelines, CSS tokens, and component patterns for Universidad
  Santiago de Cali (USC) Marketplace modules ("Versand" design kit). Use whenever
  creating, styling, refactoring, or integrating frontend interfaces, HTML templates,
  dashboards, auth screens, or UI components for the USC Marketplace to ensure 100%
  visual and architectural consistency across modules.
---

# Versand Design System - USC Marketplace

Esta skill actúa como el estándar oficial de diseño y arquitectura de interfaz para todos los módulos de software del **Marketplace de la Universidad Santiago de Cali (USC)** (Construcción de Software II).

Al activar esta skill, cualquier asistente de IA o desarrollador debe aplicar estrictamente los estilos, tokens CSS, componentes y estructuras de maquetación definidos en este repositorio para asegurar que todos los módulos desarrollados por diferentes equipos se perciban como una sola aplicación cohesiva.

---

## 1. Cuándo activar esta Skill

Usa esta skill cuando el usuario solicite:
- Crear una nueva pantalla, vista o template HTML para cualquier módulo del Marketplace USC (Ventas, Carrito, Pagos, Envíos, Inventario, Calificaciones, Notificaciones, etc.).
- Diseñar o maquetar dashboards operativos, vistas de comprador, listados de órdenes o paneles de administración.
- Crear formularios con selector de roles, inputs estilizados, modales o toasts de confirmación.
- Refactorizar o limpiar estilos CSS para alinearlos con la identidad visual oficial del proyecto.
- Adaptar interfaces existentes para que soporten modo oscuro (`data-theme="dark"`) y diseño responsive.

---

## 2. Recursos Clave del Sistema

El kit de estilos se compone de tres piezas fundamentales:
1. **Hoja de estilos principal**: [`styles/versand.css`](./styles/versand.css) - Contiene todos los tokens `:root`, modo oscuro, reset, componentes y media queries.
2. **Script de autenticación y tema**: [`scripts/versand-auth.js`](./scripts/versand-auth.js) - Contiene el SVG vectorial `logo`, el switch de tema `setupTheme()` y el contrato de autenticación mock/microservicios `callAuthService()`.
3. **Script de interacciones y trazabilidad**: [`scripts/versand-mvp.js`](./scripts/versand-mvp.js) - Gestión de modales, toasts, apertura de detalle de pedidos y etiquetas de envío imprimibles.

Documentación de referencia detallada:
- **Tokens y Colores**: [Tokens CSS](./references/tokens.md)
- **Ejemplos de Componentes**: [Catálogo de Componentes HTML](./references/components.md)
- **Directrices y Reglas**: [Reglas de Diseño](./references/guidelines.md)

---

## 3. Tokens Principales de Color y Variables

Toda interfaz debe utilizar exclusivamente las variables CSS de Versand.

```css
/* Modo Claro */
--brand: #7046c8;         /* Morado principal de marca */
--brand-dark: #4c2993;    /* Hover y acentos oscuros */
--brand-soft: #eee7ff;    /* Fondos suaves y badges destacados */
--canvas: #f7f5fb;        /* Fondo general */
--surface: #ffffff;       /* Fondo de tarjetas, tablas y paneles */
--ink: #211b35;           /* Color de texto principal */
--muted: #786f8f;         /* Color de texto secundario y subtítulos */
--line: #e6e0f0;          /* Color de bordes y separadores */
--success: #247c63;       /* Éxito / Entregado */
--warning: #a2660a;       /* Advertencia / En tránsito */
--danger: #b84b63;        /* Error / Incidencia */

/* Modo Oscuro: se aplica automáticamente al colocar data-theme="dark" en el body */
```

Para ver la tabla completa de valores hex y contraste en ambos modos, consulta [tokens.md](./references/tokens.md).

---

## 4. Arquetipos de Pantallas

Cualquier nueva vista debe seguir uno de los siguientes dos patrones:

### A. Vista Interna / Dashboard (`.shell`)
Estructura compuesta por barra lateral fija (`.sidebar`) y área principal (`.main` con `.topbar` y `.content`).

```html
<div class="shell">
  <aside class="sidebar">
    <div class="brand">
      <span class="brand-mark" id="logo"></span>
      <span>Versand</span>
    </div>
    <span class="side-label">Módulo</span>
    <nav class="nav">
      <button class="active">Vista Principal</button>
      <button>Opciones</button>
    </nav>
    <div class="sidebar-footer">Estado: Activo</div>
  </aside>

  <section class="main">
    <header class="topbar">
      <div class="topbar-title"><b>Título Módulo</b><span>Subtítulo</span></div>
      <div class="top-actions">
        <button id="themeToggle" class="icon-btn">☾</button>
        <div class="avatar">US</div>
      </div>
    </header>
    <main class="content">
      <!-- Contenido aquí -->
    </main>
  </section>
</div>
```

### B. Vista de Acceso / Login Split (`.login`)
Estructura de dos columnas: izquierda visual de marca con degradado (`.login-visual`) y derecha con formulario de credenciales y selector de rol (`.login-panel`).

Consulta el template de referencia en [`templates/login.html`](./templates/login.html).

---

## 5. Componentes Esenciales y Clases CSS

| Componente | Clase CSS | Ejemplo de uso |
| :--- | :--- | :--- |
| **Botón Primario** | `.btn .btn-primary` | Acción principal (`Guardar`, `Comprar`, `Crear`) |
| **Botón Suave** | `.btn .btn-soft` | Acción secundaria (`Cancelar`, `Detalle`, `Volver`) |
| **Botón Icono** | `.icon-btn` | Botón circular/cuadrado con icono (`☾`, `🔔`, `🔍`) |
| **Tarjeta / Panel** | `.card .panel` | Contenedor con borde `--line`, fondo `--surface` y sombra |
| **Tarjeta KPI** | `.card .kpi` | Métricas con `.kpi-label`, `.kpi-value` y `.trend .up/.down` |
| **Insignia / Badge**| `.badge .badge-[success\|warning\|danger\|info]` | Estado de pedidos o alertas con punto indicador |
| **Campo de Entrada**| `.field` envolviendo `input` o `select` | Campos de formulario con etiqueta flotante y borde interactivo |
| **Selector de Rol** | `.role-cards` con `.role-card` | Botones tipo tarjeta para selección de perfil de usuario |
| **Tabla de Datos** | `.table-card` > `.table-scroll` > `table` | Tablas con `th` en mayúsculas y filas alternables |
| **Línea de Tiempo** | `.timeline` > `.step` (`.done`, `.current`) | Trazabilidad vertical con puntos conectores `.dot` |
| **Modal / Diálogo** | `.modal-backdrop` > `.modal .card` | Ventanas flotantes centradas para formularios o confirmaciones |
| **Toast** | `.toast` | Notificación temporal en la esquina inferior derecha |

Consulta el código completo en [components.md](./references/components.md).

---

## 6. Procedimiento para Implementar en un Nuevo Módulo

Cuando un desarrollador o agente trabaje en un nuevo módulo del marketplace:

1. **Importar los archivos compartidos**:
   Copiar o enlazar la carpeta `styles/versand.css` y `scripts/versand-auth.js` en el proyecto.
2. **Estructura base del documento**:
   ```html
   <link rel="stylesheet" href="path/to/styles/versand.css">
   ```
3. **Inicializar tema y marca**:
   Al final del `<body>`, añadir:
   ```html
   <script src="path/to/scripts/versand-auth.js"></script>
   <script>
     // Inyecta el logo en los elementos .brand-mark
     document.querySelectorAll("#logo, #visualLogo, #formLogo").forEach(el => el.innerHTML = logo);
     // Activa el cambio de tema claro/oscuro
     setupTheme();
   </script>
   ```
4. **Respetar las clases existentes**:
   No inventar nuevas clases para botones, tarjetas o inputs si ya existen en `versand.css`.
5. **No introducir estilos en línea con colores estáticos**:
   Si se requiere una regla de estilo adicional, usar siempre `var(--nombre-del-token)`.

---

## 7. Reglas de Validación para el Agente (Checklist de Calidad)

Antes de entregar cualquier código o componente al usuario, verifica:
- [ ] ¿Se utiliza `versand.css` como hoja de estilos?
- [ ] ¿Los botones usan `.btn .btn-primary` o `.btn .btn-soft`?
- [ ] ¿Los badges de estado usan las clases oficiales (`badge-success`, `badge-warning`, `badge-danger`)?
- [ ] ¿Los contenedores de tarjetas usan `.card` y `.panel`?
- [ ] ¿Se mantiene la compatibilidad con modo oscuro usando `var(--surface)` e `var(--ink)`?
- [ ] ¿Se conservó el layout responsive sin alterar los media queries?
- [ ] ¿Se evitó el uso de colores hexadecimales quemados en atributos `style=""`?

