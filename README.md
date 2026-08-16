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

Los nombres van **en minúscula**: `raw.githubusercontent.com` distingue
mayúsculas y un nombre que no coincide devuelve 404 sin más aviso.

## Formato

- JPEG de calidad 95. El PNG original de esta campaña pesaba 2,19 MB y el
  JPEG 470 KB sin diferencia visible; es una imagen que se descarga al abrir
  la aplicación, y ahí el peso se nota.
- Vertical. La app la encaja entera (`BoxFit.contain`), sin recortar, sobre un
  fondo oscuro, así que no hace falta ajustarse a la forma de cada pantalla.
- Ancho útil hasta 1080 px; más no aporta.
