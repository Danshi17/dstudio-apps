# dStudios Apps

Sitio web de descargas de las aplicaciones de **dStudios**.

**Sitio:** https://danshi17.github.io/dstudio-apps/

## Aplicaciones

### TuxMusic

Reproductor de música nativo para Android, iOS, Linux y Windows. Busca en
Apple Music y Spotify, importa playlists públicas, descarga canciones para
escucharlas sin conexión y mantiene la reproducción en segundo plano.

| Plataforma | Formato | Requisitos | Versión |
| --- | --- | --- | --- |
| Android | APK directo | Android 8.0 o posterior | 1.6.3 |
| iOS | IPA sin firmar | iOS 17 o posterior; Sideloadly, AltStore o Xcode | 1.6.3 |
| Linux | Paquete `.deb` | Debian 13+ / Ubuntu 24.10+ (amd64, glibc 2.39+) | 1.3.1 |
| Windows | Instalador `.exe` | Windows 10 u 11 de 64 bits | 1.3.0 |

El IPA no está firmado por Apple: hay que firmarlo con un Apple ID antes de
instalarlo. El instalador de Windows tampoco está firmado, así que SmartScreen
puede pedir confirmación.

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
├── downloads/              APK, IPA, .deb e .exe (no versionados por ahora)
└── .nojekyll               Evita el procesado de Jekyll en GitHub Pages
```

## Publicar una nueva versión

1. Copia el binario en `downloads/`.
2. Actualiza en `index.html` la versión, el tamaño, el enlace y el SHA-256.
3. Añade el binario al repositorio (la carpeta está ignorada por defecto):
   `git add -f downloads/Nombre-Del-Archivo`
4. Haz commit y push a `main`.

Los binarios no se suben hasta que se decida publicarlos. Mientras tanto, los
botones apuntan a las rutas definitivas de `downloads/`.

### Generar el paquete de Linux

Desde el repositorio de TuxMusic:

```bash
./packaging/build-deb.sh
```

El paquete resultante se guarda en `packaging/output/` y se puede comprobar con:

```bash
sudo apt install ./TuxMusic-Linux-1.3.1.deb
```

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
