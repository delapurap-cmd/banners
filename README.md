# banners

Imágenes que More Than Modes descarga en marcha, sin publicar una versión nueva.

## Cómo funciona

La app lee el parámetro `media_banner_config` de Firebase Remote Config, en el
proyecto **more-than-modes**, y descarga la imagen que se le indique por URL.

Elige la imagen según el idioma del teléfono: `media_url_es`, `media_url_fr`,
`media_url_it`, `media_url_pt`. Quien no encaje en ninguno —inglés incluido—
ve `media_url`. Así que **con una sola imagen ya funciona**; las demás son
opcionales.

## Organización

    flyers/<campaña>/<idioma>.jpg     lo que descarga la app
    flyers/<campaña>/fuente/          el original sin comprimir, para editar

Una carpeta por campaña, y las viejas **se quedan**: cambiar de campaña es
apuntar el JSON a otra carpeta, no pisar la anterior. Así se vuelve a una de
antes en un minuto y sin rebuscar en el historial.

Los nombres van **en minúscula**: `raw.githubusercontent.com` distingue
mayúsculas y un nombre que no coincide devuelve 404 sin más aviso.

## Formato

- JPEG de calidad 95. El PNG original de la campaña de agosto pesaba 2,19 MB
  y el JPEG 470 KB sin diferencia visible; es una imagen que se descarga al
  abrir la aplicación, y ahí el peso se nota.
- Vertical. La app la encaja entera (`BoxFit.contain`), sin recortar, sobre un
  fondo oscuro, así que no hace falta ajustarse a la forma de cada pantalla.
- Ancho útil hasta 1080 px; más no aporta.

### Y si la campaña se mueve

La app **no mira el campo `media_type`** para nada: le pasa la URL a
`CachedNetworkImage` y ya. Así que GIF animado y WebP animado funcionan sin
tocar la app, igual que un JPEG.

- **GIF** es lo seguro: lo pinta cualquier versión de la app.
- **WebP animado** pesa menos y no tiene las bandas de color del GIF, que sólo
  admite 256. Va en `webp/` al lado, por si se quiere cambiar.

Con animación el peso importa el doble, porque el archivo se descarga **entero**
antes de poder enseñarse: cada mega es un segundo de pantalla en blanco con
datos móviles. Y lo que lo decide no es la calidad ni la paleta, sino cuánto se
mueve el cuadro. Medido sobre esta misma campaña, montada de tres maneras:

| | peso |
|---|---|
| todo el cuadro moviéndose en cada fotograma | 5,2 MB |
| un carrusel pasando, con el fondo quieto | 3,1 MB |
| lo que se publicó: casi todo quieto | **1,0 MB** |

## Campañas

- `agosto-2026/` — la oferta del 50 %. JPEG, y lleva a la compra.
- `v3-actualiza/` — «actualiza a la versión 3». GIF animado de 5 s en bucle:
  tres naipes con portadas de la V3 y el aviso encima, en la tipografía de la
  casa. Sale de `tools/social/gif_v3.py`, en el repositorio **mtm-website**,
  que es donde viven las portadas y las tipografías.
