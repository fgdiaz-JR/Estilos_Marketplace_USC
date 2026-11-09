# Catálogo de Componentes HTML - Versand / USC Marketplace

Este documento contiene la sintaxis HTML exacta y las combinaciones de clases para implementar cualquier interfaz con el sistema de diseño oficial de Versand para el Marketplace USC.

---

## 1. Shell Principal (Sidebar + Topbar + Contenido)

Utilizado para paneles administrativos, dashboards de operador y vistas internas de gestión.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Versand | Título del Módulo</title>
  <link rel="stylesheet" href="../styles/versand.css">
</head>
<body>
  <div class="shell">
    <!-- Barra lateral -->
    <aside class="sidebar">
      <div class="brand">
        <span class="brand-mark" id="logo"></span>
        <span>Versand</span>
      </div>
      <span class="side-label">Sección</span>
      <nav class="nav">
        <button class="active">Opción Principal</button>
        <button>Segunda Opción</button>
        <button>Incidencias <span class="badge badge-danger" style="margin-left:auto">3</span></button>
      </nav>
      <div class="sidebar-footer">
        Sistema operativo<br>
        <strong style="color: #d5c5ff">Servicios activos</strong>
      </div>
    </aside>

    <!-- Contenido principal -->
    <section class="main">
      <header class="topbar">
        <div class="topbar-title">
          <b>Nombre del Módulo</b>
          <span>Descripción corta o fecha</span>
        </div>
        <div class="top-actions">
          <button id="themeToggle" class="icon-btn" aria-label="Cambiar tema">☾</button>
          <button class="icon-btn" aria-label="Notificaciones">♢</button>
          <div class="avatar">US</div>
          <a class="btn btn-soft" href="login.html">Salir</a>
        </div>
      </header>

      <main class="content">
        <!-- Encabezado de página -->
        <div class="page-head">
          <div>
            <span class="eyebrow">Categoría</span>
            <h1>Título de la Pantalla</h1>
            <p class="lead">Explicación concisa del objetivo de este módulo.</p>
          </div>
          <div class="page-actions">
            <button type="button" class="btn btn-soft">Acción secundaria</button>
            <button type="button" class="btn btn-primary">Acción primaria</button>
          </div>
        </div>

        <!-- Inyectar aquí KPIs, tablas, paneles o gráficos -->
      </main>
    </section>
  </div>

  <script src="../scripts/versand-auth.js"></script>
  <script>
    document.querySelector("#logo").innerHTML = logo;
    setupTheme();
  </script>
</body>
</html>
```

---

## 2. Grilla de Tarjetas KPI

Diseñadas con efecto decorativo de arco circular en CSS (`.kpi:after`).

```html
<div class="kpi-grid">
  <article class="card kpi">
    <span class="kpi-label">Entregas totales</span>
    <div class="kpi-value">842</div>
    <span class="trend up">↑ 12.8% vs. semana anterior</span>
  </article>

  <article class="card kpi">
    <span class="kpi-label">Entregas a tiempo</span>
    <div class="kpi-value">94.6%</div>
    <span class="trend up">↑ 2.4% · meta: 92%</span>
  </article>

  <article class="card kpi">
    <span class="kpi-label">Tiempo promedio</span>
    <div class="kpi-value">2.8 <small>días</small></div>
    <span class="trend down">↓ 0.3 días mejor</span>
  </article>

  <article class="card kpi">
    <span class="kpi-label">Incidencias abiertas</span>
    <div class="kpi-value" style="color: var(--danger)">03</div>
    <span class="trend down">1 crítica requiere acción</span>
  </article>
</div>
```

---

## 3. Botones y Badges

### Botones
```html
<!-- Primario -->
<button type="button" class="btn btn-primary">Guardar cambios</button>

<!-- Suave / Secundario -->
<button type="button" class="btn btn-soft">Cancelar</button>

<!-- Botón de icono -->
<button type="button" class="icon-btn" aria-label="Buscar">🔍</button>
```

### Badges de Estado
Los badges incluyen un punto indicador automático mediante el pseudo-elemento `:before`.
```html
<span class="badge badge-success">Entregado</span>
<span class="badge badge-warning">En tránsito</span>
<span class="badge badge-danger">Incidencia</span>
<span class="badge badge-info">Programado</span>
```

---

## 4. Paneles y Tablas de Datos

```html
<article class="card panel table-card">
  <div class="panel-head">
    <div>
      <h2>Guías y entregas recientes</h2>
      <p class="muted">Lista detallada de despachos con trazabilidad activa</p>
    </div>
    <button class="btn btn-soft">Ver historial</button>
  </div>

  <div class="table-scroll">
    <table>
      <thead>
        <tr>
          <th>Guía</th>
          <th>Destino</th>
          <th>Transportadora</th>
          <th>Estado</th>
          <th>Última actualización</th>
          <th>Acción</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>#MCX-908172</td>
          <td>Bogotá D.C.</td>
          <td>Mercado Express</td>
          <td><span class="badge badge-warning">En reparto</span></td>
          <td>Hace 8 min</td>
          <td><button class="btn btn-soft">Detalle</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</article>
```

---

## 5. Formulario y Campos (`.field` y `.role-cards`)

```html
<form class="card panel" style="max-width: 500px">
  <div class="role-cards">
    <button type="button" class="role-card active" data-role="seller">
      <b>Vendedor</b>
      <span>Publicación y despacho</span>
    </button>
    <button type="button" class="role-card" data-role="buyer">
      <b>Comprador</b>
      <span>Búsqueda y compra</span>
    </button>
  </div>

  <label class="field">
    Nombre del producto
    <input type="text" placeholder="Ej. Audífonos Bluetooth" required>
  </label>

  <label class="field">
    Precio (COP)
    <input type="number" placeholder="Ej. 120000" required>
  </label>

  <label class="field">
    Categoría
    <select>
      <option value="tech">Tecnología</option>
      <option value="books">Libros y Papelería</option>
      <option value="food">Alimentos</option>
    </select>
  </label>

  <button type="submit" class="btn btn-primary" style="width: 100%; margin-top: 15px">
    Crear publicación
  </button>
</form>
```

---

## 6. Línea de Tiempo de Seguimiento (`.timeline`)

```html
<div class="timeline">
  <div class="step done">
    <div class="dot"></div>
    <div>
      <h4 class="step-title">Pedido confirmado</h4>
      <span class="step-time">06 oct 2026 · 09:42 AM</span>
      <p class="step-note">Pago verificado y orden generada.</p>
    </div>
  </div>

  <div class="step current">
    <div class="dot"></div>
    <div>
      <h4 class="step-title">En reparto local</h4>
      <span class="step-time">08 oct 2026 · 07:15 AM</span>
      <p class="step-note">El mensajero va en camino a la dirección destino.</p>
    </div>
  </div>

  <div class="step">
    <div class="dot"></div>
    <div>
      <h4 class="step-title">Entregado</h4>
      <span class="step-time">Pendiente</span>
    </div>
  </div>
</div>
```

---

## 7. Modal y Notificaciones Toast

### Estructura de Modal
```html
<div class="modal-backdrop">
  <div class="modal card">
    <button class="modal-close" type="button" aria-label="Cerrar">×</button>
    <h2>Confirmar despacho</h2>
    <p class="muted">¿Estás seguro de que deseas marcar este pedido como despachado?</p>
    
    <label class="field">
      Número de guía de la transportadora
      <input type="text" placeholder="MCX-123456">
    </label>

    <div class="modal-actions">
      <button type="button" class="btn btn-soft">Cancelar</button>
      <button type="button" class="btn btn-primary">Confirmar</button>
    </div>
  </div>
</div>
```

### Notificación Toast
```html
<div class="toast">Guía MCX-908172 copiada al portapapeles.</div>
```

