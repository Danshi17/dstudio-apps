# dStudios Apps

Sitio web de descargas de las aplicaciones de **dStudios**.

**Sitio:** https://danshi17.github.io/dstudio-apps/

## Aplicaciones

### TuxMusic

Reproductor de música nativo para Android e iOS. Busca en Apple Music y
Spotify, importa playlists públicas, descarga canciones para escucharlas sin
conexión y mantiene la reproducción en segundo plano.

- Android 8.0 o posterior (APK directo).
- iOS 17 o posterior (IPA sin firmar; requiere Sideloadly, AltStore o Xcode).

## Estructura

```text
.
├── index.html              Página de descargas
├── assets/
│   ├── css/style.css       Estilos base heredados del sitio de plugins
│   ├── css/apps.css        Estilos propios de esta página
│   ├── js/main.js          Tema claro/oscuro y animaciones
│   ├── apps/               Iconos de TuxMusic
│   └── logo.png            Logo de dStudios
├── downloads/              APK e IPA (no versionados por ahora)
└── .nojekyll               Evita el procesado de Jekyll en GitHub Pages
```

## Publicar una nueva versión

1. Copia el APK o el IPA en `downloads/`.
2. Actualiza en `index.html` la versión, el tamaño, el enlace y el SHA-256.
3. Añade el binario al repositorio (la carpeta está ignorada por defecto):
   `git add -f downloads/Nombre-Del-Archivo`
4. Haz commit y push a `main`.

Los binarios no se suben hasta que se decida publicarlos. Mientras tanto, los
botones apuntan a las rutas definitivas de `downloads/`.

## GitHub Pages

El sitio se publica desde la rama `gh-pages`. El workflow
`.github/workflows/deploy.yml` copia el contenido de `main` a `gh-pages` en
cada push, así que **`main` es la única rama que hay que editar**.

La primera publicación se hizo creando la rama `gh-pages`; GitHub Pages la
detectó y activó automáticamente. Si alguna vez hay que revisar la
configuración: **Settings → Pages → Build and deployment → Deploy from a
branch → `gh-pages` → `/ (root)`**.

## Licencia

Apache License 2.0. Consulta [LICENSE](LICENSE).
