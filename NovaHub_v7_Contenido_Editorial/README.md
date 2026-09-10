# NovaHub v7 — Contenido Editorial + SEO

MVP de un Hub público de personajes virtuales de ficción, preparado para crecer hacia monetización con publicidad, afiliados, patrocinios u otros proveedores.

## Qué añade esta versión
- Página de inicio con contenido y navegación clara.
- Perfiles públicos server-rendered en `/modelo/:slug`.
- Artículos server-rendered en `/contenido/:slug` con texto original, categoría, meta description y JSON-LD Article.
- 6 publicaciones de ejemplo y 2 personajes ficticios.
- Página Sobre NovaHub y política editorial.
- Sitemap dinámico con perfiles y artículos.
- robots.txt dinámico.
- Open Graph y canonical URLs.
- Identificación visible de personajes ficticios.
- Deduplicación básica de eventos para evitar inflar métricas por recargas rápidas.
- Panel de métricas y registro de ingresos de v6 conservados.
- Espacio publicitario preparado, sin IDs falsos.

## Variables de entorno
- `PORT` — puerto del servidor.
- `DB_PATH` — ruta de SQLite.
- `ADMIN_KEY` — clave para `/api/stats` y `/api/revenue`. Cambiar obligatoriamente antes de producción.
- `PUBLIC_URL` — dominio público completo, por ejemplo `https://tudominio.com`.

## Ejecutar
```bash
npm install
ADMIN_KEY="una-clave-larga-y-unica" PUBLIC_URL="https://tudominio.com" npm start
```

## Monetización
El proyecto **no genera dinero automáticamente por visitas**. Primero debes conectar un proveedor real y cumplir sus políticas. Para AdSense, Google exige contenido original y útil, navegación clara y un sitio suficientemente construido; también advierte contra páginas con poco contenido o contenido generado automáticamente sin valor añadido.

No coloques datos bancarios ni llaves de pago dentro del código del sitio. Configura los datos de cobro directamente en el proveedor de monetización.

## Próximo paso de producción
1. Comprar/configurar dominio.
2. Desplegar en un hosting Node (Render, Railway, VPS, etc.).
3. Definir `PUBLIC_URL` y `ADMIN_KEY` en variables privadas.
4. Publicar más contenido original y revisar cada pieza.
5. Conectar el proveedor publicitario real cuando el sitio esté listo.
6. Configurar cobros directamente dentro del proveedor.
