# Sin Fondo — cómo obtener el APK

Proyecto Capacitor: envuelve la app web (`www/`) en un WebView Android. Todo el procesamiento ocurre en el dispositivo, sin internet.

## Opción A (la más fácil): compilar en GitHub y descargar desde el móvil

1. Crea un repositorio en GitHub y sube todo el contenido de esta carpeta (incluida `.github/`).
2. Al hacer push a `main`, GitHub compila el APK solo (pestaña **Actions**, ~3-5 min).
   También puedes lanzarlo a mano: Actions → Build APK → *Run workflow*.
3. Desde el móvil abre el repo → **Releases** → **Sin Fondo (última versión)** → descarga `app-debug.apk`.
4. Ábrelo y permite "instalar apps de orígenes desconocidos" cuando Android lo pida.

## Opción B: compilar en tu PC

Requisitos: Node 18+, Android Studio (con SDK) y JDK 17.

```bash
npm install
npx cap add android
npx cap sync android
npx cap open android
```

En Android Studio: Build → Build APK(s). Sale en
`android/app/build/outputs/apk/debug/app-debug.apk`.
O conecta el móvil por USB (depuración USB activada) y pulsa ▶ Run.

## Notas

- Tras editar `www/index.html`: `npx cap sync android` antes de recompilar.
- appId: `com.hugo.sinfondo` (cámbialo en `capacitor.config.json` antes del primer `cap add android` si quieres otro).
- El APK "debug" vale para uso personal; para distribuir hay que firmarlo (Build → Generate Signed Bundle / APK).
