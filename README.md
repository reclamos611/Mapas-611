# Territorios de Ventas

Sistema para visualizar puntos de venta, zonas por vendedor y día, con búsqueda de direcciones.

## Estructura

```
territorios/
├── index.html          ← Vista pública (lo que ven todos)
├── admin/
│   └── index.html      ← Panel admin (solo vos)
└── data/
    ├── puntos.json     ← Datos de clientes (generado desde el admin)
    └── zonas.json      ← Polígonos de zonas (generado desde el admin)
```

## Cómo publicar en GitHub Pages

### 1. Crear el repositorio

1. Entrá a [github.com](https://github.com) → **New repository**
2. Nombre: `territorios-ventas` (o el que quieras)
3. Visibilidad: **Public**
4. **No** marques "Add README"
5. Click en **Create repository**

### 2. Subir los archivos

**Opción A — desde la web de GitHub (más fácil):**

1. En el repo recién creado, click en **"uploading an existing file"**
2. Arrastrá todos los archivos manteniendo la estructura de carpetas:
   - `index.html`
   - `admin/index.html`
   - `data/puntos.json`
   - `data/zonas.json`
3. Click en **Commit changes**

**Opción B — desde la terminal:**

```bash
cd territorios
git init
git add .
git commit -m "primer commit"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/territorios-ventas.git
git push -u origin main
```

### 3. Activar GitHub Pages

1. En el repo → **Settings** → **Pages** (barra lateral izquierda)
2. Source: **Deploy from a branch**
3. Branch: **main** / **/ (root)**
4. Click en **Save**
5. Esperar 2-3 minutos → tu URL será:
   `https://TU_USUARIO.github.io/territorios-ventas/`

---

## Flujo de trabajo

### Primera vez (cargar datos)

1. Abrí `https://TU_USUARIO.github.io/territorios-ventas/admin/`
2. Click en la pestaña **Datos** → cargá tu Excel/CSV
3. Mapeá las columnas y hacé click en **Importar**
4. Click en **↓ Descargar puntos.json**
5. Subí ese archivo a la carpeta `data/` de tu repo en GitHub

### Dibujar zonas

1. En el admin, usá el ícono de **polígono** en el mapa (barra izquierda)
2. Dibujá la zona trazando puntos (doble click para cerrar)
3. Completá: nombre, vendedor y día
4. O usá **✦ Auto-generar zonas** para crear polígonos automáticos (convex hull) por vendedor+día
5. Ajustá los bordes si querés (botón de edición en la barra del mapa)
6. Click en **↓ Exportar zonas.json**
7. Subí ese archivo a la carpeta `data/` de tu repo en GitHub

### Actualizar datos

Cada vez que cambien los puntos de venta:
1. Importá el nuevo Excel en el admin
2. Descargá `puntos.json` actualizado
3. Reemplazá el archivo en GitHub → los usuarios ven los datos nuevos automáticamente

---

## Formato del Excel/CSV

| Columna | Descripción | Ejemplo |
|---------|-------------|---------|
| `numero_cliente` | ID del cliente | 1042 |
| `nombre_cliente` | Nombre del cliente | Farmacia Central |
| `numero_vendedor` | ID del vendedor | V03 |
| `nombre_vendedor` | Nombre del vendedor | Juan Pérez |
| `latitud` | Latitud decimal | -34.6037 |
| `longitud` | Longitud decimal | -58.3816 |
| `dia_visita` | Día de la semana | Lunes |

Los nombres de columna son flexibles — el sistema los detecta automáticamente.

---

## Proteger el panel admin

El admin no tiene contraseña por defecto (es una app estática). Para protegerlo:

**Opción simple:** Cambiá la URL del admin a algo difícil de adivinar, por ejemplo renombrá la carpeta `admin` a `admin-x7k9p2`.

**Opción más segura:** Usá [Netlify](https://netlify.com) en lugar de GitHub Pages → tiene protección por contraseña en el plan gratuito.

---

## Preguntas frecuentes

**¿Cuántos usuarios puede soportar?**
GitHub Pages soporta hasta 100GB de tráfico mensual. Para una app estática con 10-50 usuarios es más que suficiente.

**¿Los datos son privados?**
Los archivos en `data/` son públicos (cualquiera con la URL los puede ver). No subas datos sensibles. Si necesitás privacidad, usá un repo privado + Netlify.

**¿Se actualiza en tiempo real?**
No. Cuando subís un nuevo `puntos.json` o `zonas.json`, los usuarios ven los datos nuevos al recargar la página (puede tardar unos minutos en propagarse por el CDN de GitHub).
