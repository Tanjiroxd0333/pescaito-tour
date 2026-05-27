# Pescaito Tour — Tour Virtual 360°

Tour virtual interactivo en 360° de **Pescaito**, accesible directamente desde el navegador. El proyecto está generado con la tecnología de [3DVista](https://www.3dvista.com/) y se distribuye como un sitio web estático.

## 🌐 Demo

Una vez desplegado, el tour estará disponible en la URL que entregue el proveedor de hosting (Cloudflare Pages / Vercel / Netlify).

## 📂 Estructura del proyecto

```
.
├── index.htm              # Punto de entrada del tour
├── script.js              # Script principal generado por 3DVista
├── script_general.js      # Script de soporte
├── tdvplayersw.js         # Service worker del player
├── files.json             # Manifiesto de assets del tour
├── favicon.ico
├── manifest.json
├── browserconfig.xml
├── thumbnail.png
├── lib/                   # Librerías del player 3DVista (~22 MB)
├── locale/                # Archivos de localización (i18n)
├── media/                 # Panorámicas, imágenes y recursos del tour (~225 MB)
└── misc/                  # Iconos y recursos varios
```

> Los archivos binarios grandes (`Pescaito Tour_Windows.exe`, `Pescaito Tour_quest3.ts`, `Pescaito Tour.tar.bz2`) están excluidos del repositorio mediante `.gitignore`. Son builds para otras plataformas (Windows desktop y Meta Quest 3) y no se necesitan para la versión web.

## 🚀 Ejecución local

Como el tour usa rutas relativas y `fetch` para cargar assets, **debe servirse mediante un servidor HTTP local** (no funciona abriendo `index.htm` con doble clic por restricciones CORS del navegador).

### Opción 1 — Python (incluido en macOS / Linux / Windows con Python)

```bash
python -m http.server 8080
```

Luego abre <http://localhost:8080/index.htm>.

### Opción 2 — Node.js

```bash
npx serve .
```

### Opción 3 — VS Code

Instala la extensión **Live Server** y haz clic derecho sobre `index.htm` → *Open with Live Server*.

## ☁️ Despliegue

El proyecto es estático, por lo que se puede desplegar en cualquier hosting de sitios estáticos:

| Plataforma | Plan gratuito | SSL automático | Recomendado para este proyecto |
|---|---|---|---|
| **Cloudflare Pages** | Sí, generoso | Sí | ✅ Mejor para los ~247 MB del tour |
| **Vercel** | 100 MB de despliegue | Sí | ⚠️ Hobby excede límite; Pro: $20/mes |
| **Netlify** | Sí | Sí | ✅ Funciona |
| **GitHub Pages** | Sí, hasta 1 GB | Sí | ✅ Funciona, sin builds de servidor |

### Despliegue rápido en Cloudflare Pages

1. Entra en <https://pages.cloudflare.com> e inicia sesión.
2. **Create a project → Connect to Git** y elige este repositorio.
3. Configuración del build:
   - **Framework preset:** *None*
   - **Build command:** *(vacío)*
   - **Build output directory:** `/`
4. **Save and Deploy**. Cloudflare emite SSL automáticamente.

## 🛠️ Tecnologías

- HTML5 / CSS3 / JavaScript (Vanilla)
- 3DVista Virtual Tour Player
- WebGL para renderizado de panorámicas 360°
- Service Worker para caching offline

## 📄 Licencia

Todos los derechos reservados. Contenido y assets propiedad de sus respectivos autores.
