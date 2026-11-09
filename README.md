# Estilos Marketplace USC (Versand Design System & Agent Skill)

Kit visual compartido y **Agent Skill oficial** para los módulos de desarrollo del Marketplace de la Universidad Santiago de Cali (Construcción de Software II).

Permite que cualquier persona o **asistente de Inteligencia Artificial (Antigravity, Claude Code, Cursor, Codex, OpenCode, etc.)** descargue o instale este repositorio como una *Skill* y automáticamente aplique las mismas convenciones visuales, tokens de color, componentes HTML y directrices de maquetación en cualquier módulo del proyecto.

---

## 🚀 ¿Cómo usar este repositorio como una Skill para IA?

Cuando un asistente de IA carga esta skill, lee [`SKILL.md`](./SKILL.md) y asume el rol de **Lead Frontend Architect** del Marketplace USC, garantizando que todo el código generado cumpla estrictamente con la identidad visual compartida.

### Opción 1: En proyectos con Antigravity / Google Agents
Puedes instalar la skill en tu proyecto de cualquiera de las siguientes formas:

1. **Como submódulo o carpeta de skills de tu proyecto**:
   Copia este repositorio dentro de `.agents/skills/marketplace-usc-styles/`:
   ```bash
   git submodule add https://github.com/fgdiaz-JR/Estilos_Marketplace_USC.git .agents/skills/marketplace-usc-styles
   ```
2. **Como skill global en tu máquina**:
   Clona el repositorio en la carpeta global de skills de Antigravity:
   ```bash
   git clone https://github.com/fgdiaz-JR/Estilos_Marketplace_USC.git ~/.gemini/config/skills/marketplace-usc-styles
   ```

### Opción 2: En Claude Code o CLI Agents
Copia el repositorio dentro de tu directorio de skills local del proyecto:
```bash
git clone https://github.com/fgdiaz-JR/Estilos_Marketplace_USC.git .claude/skills/marketplace-usc-styles
```

### Opción 3: En Cursor / Windsurf / Copilot
Agrega una referencia en tu archivo `.cursorrules` o prompt del proyecto:
> "Sigue las directrices de diseño y componentes definidos en `SKILL.md` del repositorio Estilos_Marketplace_USC."

---

## 📂 Estructura del Repositorio

```text
├── SKILL.md                 # Definición principal de la Skill con frontmatter y directrices de IA
├── references/              # Guías detalladas leídas bajo demanda por los agentes
│   ├── tokens.md            # Especificación exhaustiva de tokens CSS, colores y tipografía
│   ├── components.md        # Snippets HTML listos para copiar/generar de todos los componentes
│   └── guidelines.md        # Reglas estrictas de diseño, responsive y modo oscuro
├── styles/
│   └── versand.css          # Hoja de estilos con variables CSS, layouts responsive y reset
├── scripts/
│   ├── versand-auth.js      # Logo SVG oficial, toggle de tema oscuro y contrato de autenticación
│   └── versand-mvp.js       # Trazabilidad interactiva, modales, toasts y etiquetas imprimibles
├── templates/               # Pantallas demo de referencia funcional
│   ├── login.html           # Login con split visual y selector de rol
│   ├── operator-dashboard.html # Dashboard operativo de entregas (patrón .shell)
│   ├── buyer-orders.html    # Seguimiento de pedidos para el comprador
│   └── redirect.html        # Redirección compatible
└── .agents/
    └── skills/
        └── marketplace-usc-styles/
            └── SKILL.md     # Entrada directa autodescubrible para Antigravity
```

---

## 🎨 Convenciones Visuales y Tokens

| Concepto | Token CSS | Valor (Modo Claro) | Descripción |
| :--- | :--- | :--- | :--- |
| **Marca Principal** | `--brand` | `#7046c8` | Morado corporativo para botones primarios y acentos |
| **Hover de Marca** | `--brand-dark` | `#4c2993` | Estados de hover y foco activo |
| **Marca Suave** | `--brand-soft` | `#eee7ff` | Fondos de banners y acentos sutiles |
| **Color Secundario**| `--violet` | `#a074ee` | Violeta de apoyo para gráficos y avatares |
| **Fondo Lienzo** | `--canvas` | `#f7f5fb` | Fondo general de la página |
| **Superficie** | `--surface` | `#ffffff` | Fondo de tarjetas (`.card`), modales y tablas |
| **Texto Principal** | `--ink` | `#211b35` | Títulos y contenido principal |
| **Texto Atenuado** | `--muted` | `#786f8f` | Subtítulos, labels y metadatos |
| **Líneas y Bordes** | `--line` | `#e6e0f0` | Divisores y bordes |
| **Éxito** | `--success` | `#247c63` | Pedidos entregados / KPIs positivos |
| **Alerta / Espera** | `--warning` | `#a2660a` | En tránsito / estados pendientes |
| **Error / Peligro** | `--danger` | `#b84b63` | Incidencias / cancelaciones |

Para habilitar el **Tema Oscuro**, agrega `data-theme="dark"` al elemento `<body>`. Los tokens se reasignan automáticamente.

---

## 💻 Uso Tradicional en Otro Módulo

1. Copia las carpetas `styles/` y `scripts/` a tu módulo.
2. Vincula la hoja de estilos en el `<head>`:
   ```html
   <link rel="stylesheet" href="../styles/versand.css">
   ```
3. Reutiliza los componentes del [Catálogo de Componentes](./references/components.md).
4. No introduzcas colores hexadecimales aislados; usa siempre las variables de `:root`.
5. Inicializa el logo y el toggle de tema con `versand-auth.js`.

---

## 📜 Licencia

Uso académico y colaborativo para la Universidad Santiago de Cali (USC).
