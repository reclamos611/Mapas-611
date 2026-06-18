# Mapas 611 — Territorios de Ventas

Sistema para visualizar puntos de venta y zonas por vendedor/día.

## Archivos del repo

```
Mapas-611/
├── index.html      ← Vista pública (lo ven todos)
├── admin.html      ← Panel admin (solo vos)
├── puntos.json     ← Datos de clientes
└── zonas.json      ← Polígonos de zonas
```

## Activar GitHub Pages

1. En el repo → **Ajustes** → **Pages**
2. Branch: **principal** / **/ (root)**
3. Click **Save**
4. URL pública: `https://reclamos611.github.io/Mapas-611/`
5. Panel admin: `https://reclamos611.github.io/Mapas-611/admin.html`

## Cómo cargar datos

### Puntos de venta (Excel/CSV)
1. Abrí `admin.html`
2. Pestaña **Datos** → cargá tu Excel
3. Mapeá columnas → **Importar**
4. Click **↓ Descargar puntos.json**
5. En GitHub: clic en `puntos.json` → ícono lápiz ✏️ → pegá el contenido → Commit

### Zonas por vendedor+día
1. En `admin.html`, usá el polígono 🖊️ del mapa
2. Dibujá la zona → asignás vendedor + día
3. O usá **✦ Auto-generar zonas** (crea convex hull por vendedor+día)
4. **↓ Exportar zonas.json** → subí a GitHub igual que puntos.json

## Formato Excel esperado

| Columna | Ejemplo |
|---------|---------|
| numero_cliente | 1042 |
| nombre_cliente | Farmacia Central |
| numero_vendedor | V03 |
| nombre_vendedor | Juan Pérez |
| latitud | -34.6037 |
| longitud | -58.3816 |
| dia_visita | Lunes |
