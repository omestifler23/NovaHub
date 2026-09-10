# NovaHub — paso a producción real

## Arquitectura recomendada para el lanzamiento inicial

- Hosting: Render Web Service.
- Backend: Node.js + Express.
- Base de datos: SQLite sobre disco persistente de Render.
- Instancias: 1.
- Dominio: dominio propio conectado a Render.
- Monetización: proveedor publicitario/afiliación aprobado; no se inventa ningún ID de publisher.

> Para una primera versión con tráfico bajo, esta arquitectura es simple. Si el tráfico crece o quieres varias instancias, migra la base de datos a PostgreSQL.

## 1. Crear el repositorio

1. Crea un repositorio privado en GitHub, por ejemplo `novahub`.
2. Descomprime este proyecto.
3. Sube todos los archivos a la raíz del repositorio.
4. No subas `.env`, credenciales, claves bancarias ni identificadores privados.

## 2. Crear el servicio en Render

1. En Render: New → Web Service.
2. Conecta el repositorio de GitHub.
3. Render detectará `render.yaml`.
4. El servicio usa `npm install` para build y `npm start` para arrancar.
5. El disco persistente queda montado en `/var/data` y la base en `/var/data/novahub.db`.
6. El health check es `/health`.

## 3. Variables obligatorias

Configura en Render:

- `PUBLIC_URL=https://TU-DOMINIO.COM`
- `ADMIN_KEY` se genera automáticamente en el Blueprint.
- `DB_PATH=/var/data/novahub.db`

Nunca pongas una clave bancaria o financiera en estas variables.

## 4. Dominio

1. Compra un dominio que represente la marca.
2. En Render → Settings → Custom Domains, añade el dominio.
3. Configura en tu registrador los DNS que Render indique.
4. Verifica el dominio.
5. Render gestiona el certificado TLS/HTTPS del dominio.
6. Después cambia `PUBLIC_URL` al dominio definitivo y vuelve a desplegar.

## 5. Comprobación antes de monetizar

Verifica:

- `/`
- `/modelo/luna`
- `/modelo/aria`
- `/contenido/luna-estilo-sin-complicarse`
- `/sitemap.xml`
- `/robots.txt`
- `/health`
- `/about.html`
- `/privacy.html`
- `/terms.html`
- `/contact.html`

También comprueba desde el móvil que la navegación funciona y que no hay páginas vacías.

## 6. AdSense / proveedor de anuncios

No pongas anuncios reales todavía hasta que el dominio esté publicado y el contenido esté revisado.

Cuando tengas la cuenta del proveedor:

1. Añade el dominio real.
2. Completa la verificación de propiedad.
3. Añade el código que entregue el proveedor.
4. Si el proveedor solicita `ads.txt`, usa exactamente la línea que él entregue.
5. No inventes un `pub-...`.

## 7. Importante sobre ingresos

Las visitas no generan dinero automáticamente. El ingreso aparece cuando un proveedor de monetización sirve anuncios, afiliación, patrocinios u otra fuente y registra el resultado.

NovaHub ya dispone de tracking para sesiones, campañas, vistas, clics y revenue importado.

## 8. Siguiente etapa después del lanzamiento

Cuando el dominio esté activo:

1. Conectar proveedor publicitario.
2. Conectar Search Console.
3. Revisar indexación y sitemap.
4. Publicar contenido de forma constante.
5. Revisar Analytics/UTM.
6. Cuando haya tráfico suficiente, evaluar PostgreSQL y CDN para escalar.
