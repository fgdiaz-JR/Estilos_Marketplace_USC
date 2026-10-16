# Estilos Marketplace USC

Kit visual compartido para los módulos del marketplace de la Universidad Santiago de Cali. Los templates y componentes usan la misma identidad visual para que los módulos de los diferentes grupos se perciban como una sola aplicación.

## Estructura

```text
styles/
  versand.css                 # Tokens, componentes y layouts responsive
scripts/
  versand-auth.js             # Logo SVG y cambio de tema
  versand-mvp.js              # Interacciones de seguimiento y modales
templates/
  login.html                  # Inicio de sesión y selección de rol
  operator-dashboard.html     # Dashboard operativo
  buyer-orders.html           # Pedidos y trazabilidad del comprador
  redirect.html               # Entrada compatible con enlaces antiguos
```

## Uso en otro módulo

1. Copia `styles/`, `scripts/` y los templates que necesites a tu módulo.
2. Conserva las rutas relativas o actualiza los enlaces a `versand.css` y a los scripts compartidos.
3. Reemplaza textos, datos y acciones del demo sin cambiar las clases visuales existentes.
4. Usa los tokens CSS de `:root` para ampliar la interfaz sin introducir colores o espaciados aislados.

Los templates son HTML estático y se pueden abrir directamente en el navegador. El login funciona con una sesión demo cuando los microservicios no están disponibles; para un módulo real, reemplaza `callAuthService` por el contrato de autenticación del equipo.

## Convenciones visuales

- Primario: morado `--brand`.
- Superficie y canvas: `--surface` y `--canvas`.
- Estados: `--success`, `--warning` y `--danger`.
- Componentes: `.btn`, `.card`, `.badge`, `.kpi`, `.panel`, `.field` y `.nav`.
- Tema oscuro: agrega `data-theme="dark"` al elemento `body`.

## Licencia

Uso académico y colaborativo para los módulos del marketplace USC.
