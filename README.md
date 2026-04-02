# 📱 Formaciones FeSMC UGT CLM

PWA reutilizable para comunicar acciones formativas y jornadas de FeSMC UGT Castilla-La Mancha.

🌐 **Producción:** [https://jornadasformacion-fesmc-clm.netlify.app](https://jornadasformacion-fesmc-clm.netlify.app)

---

## 📁 Estructura del proyecto

```
formaciones/
├── index.html              ← Página principal (la que se publica)
├── indexpwaformacion.html  ← Plantilla / versión de respaldo
├── manifest.json           ← Configuración PWA (nombre, colores, iconos)
├── sw.js                   ← Service Worker (caché offline)
├── fondo.png               ← Imagen de fondo fija (parallax)
├── qr.jpeg                 ← Código QR del formulario de inscripción
├── icon-192.png            ← Icono PWA para pantalla de inicio (móvil)
└── icon-512.png            ← Icono PWA alta resolución (splash screen)
```

---

## ♻️ Cómo reutilizar para una nueva formación

Para adaptar el proyecto a una nueva jornada o acción formativa, solo tienes que modificar **4 elementos**:

### 1. `index.html` — Contenido de la jornada

Localiza y actualiza estos bloques:

| Qué cambiar | Dónde buscarlo en el HTML |
|---|---|
| Título de la formación | `<h1 class="hero-title">` |
| Subtítulo / descripción | `<p class="hero-subtitle">` y sección "Sobre la jornada" |
| Fecha, horario y lugar | Bloque `info-strip` (los tres `<div class="info-cell">`) |
| Público destinatario | Las tres `<div class="audience-pill">` |
| Módulos del programa | Los 5 `<div class="module-item">` con su contenido `<ul>` |
| Info práctica | Sección "Información práctica" (`prac-row`) |
| Enlace al formulario | Atributo `href` del `<a class="mega-qr-link">` |
| Nombre del firmante | Bloque `signed-block` al final |

### 2. `fondo.png` — Imagen de fondo

Sustituye el archivo por una imagen representativa de la nueva formación. Recomendaciones:
- Formato: PNG o JPG
- Orientación: vertical o cuadrada
- La app aplica automáticamente oscurecimiento y desenfoque, así que no importa si es muy colorida

### 3. `qr.jpeg` — Código QR

Genera el QR del nuevo formulario de inscripción (Google Forms u otro) y reemplaza el archivo. Herramientas gratuitas: [qr-code-generator.com](https://www.qr-code-generator.com) o [qrcode-monkey.com](https://www.qrcode-monkey.com).

### 4. `manifest.json` — Nombre de la app

Actualiza `name` y `description` para que la PWA instalada en el móvil muestre el nombre correcto:

```json
{
  "name": "Nombre de la nueva formación",
  "short_name": "Formación UGT",
  "description": "Descripción breve — fecha y lugar",
  ...
}
```

---

## 🚀 Publicación en Netlify

El proyecto se despliega automáticamente desde este repositorio de GitHub.

1. Haz los cambios en los archivos
2. Haz commit y push a la rama `main`
3. Netlify detecta el cambio y publica en menos de 1 minuto
4. La URL permanece siempre igual: `https://jornadasformacion-fesmc-clm.netlify.app`

---

## 📲 Instalación como PWA

Cuando un usuario abre la web desde el móvil:
- **Android (Chrome):** aparece el banner "Añadir a pantalla de inicio" automáticamente
- **iPhone (Safari):** pulsar el botón compartir → "En la pantalla de inicio"

Una vez instalada funciona **sin conexión** gracias al Service Worker (`sw.js`).

---

## 🎨 Identidad visual

| Elemento | Valor |
|---|---|
| Color principal | `#C8102E` (rojo UGT) |
| Color acento | `#E8A020` (dorado) |
| Fondo base | `#141010` (negro cálido) |
| Fuente títulos | Oswald |
| Fuente cuerpo | Barlow / Barlow Condensed |

---

## 📌 Notas

- `indexpwaformacion.html` se mantiene como **plantilla limpia** de referencia. No sobreescribir.
- El Service Worker cachea los archivos para uso offline. Si actualizas `fondo.png` o `qr.jpeg` con el mismo nombre de archivo, fuerza el refresco en el navegador o incrementa la versión del caché en `sw.js` (`const CACHE_NAME = 'fesmcugt-v2'`).

---

## 🤖 Prompt de inicio para actualizar con IA

Cuando vayas a actualizar el proyecto para una nueva formación, abre una conversación nueva con Claude y empieza pegando este mensaje. Luego adjunta los archivos indicados:

---

> Tengo una PWA publicada en Netlify que uso para comunicar acciones formativas de FeSMC UGT CLM.
> Necesito actualizar el proyecto para una nueva jornada.
>
> Te paso:
> - El `README.md` del proyecto (para que entiendas la estructura)
> - El `index.html` actual (para que edites sobre él)
> - [La circular en PDF con los datos de la nueva jornada **y/o** los datos sueltos abajo]
>
> Quiero que me devuelvas:
> 1. El `index.html` actualizado con los nuevos datos
> 2. Aviso si hay que cambiar algo en `manifest.json`
> 3. Aviso si hay que incrementar la versión del caché en `sw.js`
>
> Datos de la nueva jornada:
> - **Título:** …
> - **Fecha:** …
> - **Horario:** …
> - **Lugar:** …
> - **Público:** …
> - **Módulos / programa:** …
> - **Info práctica:** …
> - **Enlace formulario de inscripción:** …
> - **Firmante:** …
>
> Archivos que adjunto en este mensaje: `README.md` · `index.html` · [circular PDF si la tienes]

---

> 💡 **Consejo:** si tienes la circular en PDF, no hace falta rellenar los campos uno a uno — Claude extrae todos los datos directamente del documento.

---

*FeSMC UGT Castilla-La Mancha · Secretaría de Acción Sindical*
