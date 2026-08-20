# Catálogo · Electrolux San Pedro

Catálogo web con la marca de la tienda que muestra productos **sin precios**,
con llamado a la acción para **ir a la tienda**, y que se **actualiza solo una
vez al día** con los productos e imágenes de shopclub.

## Qué hay aquí

- **index.html** — el catálogo (marca San Pedro, filtro por categoría + marca + búsqueda, imágenes encuadradas, botón "Verlo en tienda" y "Cómo llegar").
- **armar_catalogo_auto.py** — descubre TODO el catálogo de la tienda automáticamente (sin lista) y, reutilizando el Extractor OLB, escribe productos.json con las imágenes.
- **extractor_olb.py** — tu Extractor OLB (lo usa el script de arriba para las imágenes).
- **.github/workflows/sync.yml** — corre el script una vez al día, solo.
- **productos.json** — lo genera el script; es lo que muestra el catálogo.
- **extractor_manual/** — el Extractor OLB completo para consultas puntuales por modelo/SAP (opcional, no interviene en lo automático).

## Publicar / actualizar en tu repositorio de GitHub

Ya tienes el repositorio creado. Para dejar esta versión:

1. Sube al **raíz** del repositorio: `index.html`, `armar_catalogo_auto.py` y `extractor_olb.py` (reemplazando los que estén).
2. Abre `.github/workflows/sync.yml` en GitHub y reemplaza su contenido por el de este archivo (ahora usa Python).
3. Puedes borrar `sync.js` (ya no se usa).
4. Confirma **Settings → Actions → General → Workflow permissions → Read and write**.
5. Pestaña **Actions → Actualizar catálogo → Run workflow**. Genera productos.json con tus productos e imágenes reales.
6. **Settings → Pages** → rama `main`, carpeta `/ (root)` para publicar el sitio.

De ahí en adelante se actualiza solo cada día.

## Ajustes rápidos

- **Datos de la tienda** (nombre, WhatsApp, dirección, mapa): constante `CONFIG` al final de index.html. El WhatsApp ya es el +56 9 8923 6138.
- **Color de marca:** variable `--accent` arriba de index.html.
- **Marcas incluidas / tamaño de imagen / n° de imágenes:** al inicio de armar_catalogo_auto.py (`MARCAS`, `IMG_LADO`, `MAX_IMAGENES`).
- **Hora de actualización:** línea `cron` en sync.yml.

## Uso manual del Extractor (opcional)

Dentro de `extractor_manual/`:

    python extractor_olb.py EFLWD12O DM6SB FE4SXC --descargar

Sirve para revisar o descargar imágenes/fichas de productos puntuales.
