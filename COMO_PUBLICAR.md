# Publicar la web de BattleBots Arena (gratis, con dirección https real)

Esta carpeta es la web completa: `index.html` + `hero.jpg`. No necesita servidor ni base de datos: cualquier hosting
de páginas estáticas la sirve tal cual. El botón de descarga apunta a `DOWNLOAD_URL` (línea `const DOWNLOAD_URL = ""`
casi al final de `index.html`): cuando tengas el enlace del zip, pégalo entre las comillas.

## Opción A (recomendada): GitHub Pages + GitHub Releases

Sirve para la web Y para el zip del juego (un "release" admite archivos de hasta 2 GB).

1. Crea una cuenta en https://github.com (si no tienes).
2. Instala GitHub CLI: en PowerShell `winget install GitHub.cli`, cierra y abre la terminal, y ejecuta `gh auth login`
   (elige GitHub.com, HTTPS, y entra con tu navegador).
3. Avísame: con `gh` conectado creo el repositorio `battlebots-arena`, subo la web, activo Pages y publico el zip
   como release. La dirección queda como `https://TU_USUARIO.github.io/battlebots-arena/`.

Si prefieres hacerlo a mano: repositorio nuevo público → "Add file / Upload files" → sube `index.html` y `hero.jpg` →
Settings → Pages → Source "Deploy from a branch", rama `main`, carpeta `/ (root)` → Save. El zip va en
"Releases → Draft a new release → Attach binaries". Copia el enlace del zip y pégalo en `DOWNLOAD_URL`.

## Opción B: itch.io (la típica para compartir juegos)

1. Cuenta en https://itch.io → "Upload new project".
2. Kind of project: Downloadable. Sube `Builds/BattleBots_Windows.zip` (límite 1 GB) y marca "Windows".
3. Pega el texto de la web en la descripción y sube `hero.jpg` como portada. itch te da `https://TU_USUARIO.itch.io/battlebots-arena`.

## Opción C: Netlify Drop (solo la web, en un minuto)

1. Abre https://app.netlify.com/drop y arrastra esta carpeta entera.
2. Te da una dirección `https://algo.netlify.app` al instante (crea la cuenta gratis para que no caduque).
3. El zip del juego es grande para Netlify: déjalo en GitHub Releases, itch.io o un enlace de OneDrive y ponlo en `DOWNLOAD_URL`.

## Generar el zip del juego

En Unity: `BattleBots > 10 - Build Windows (zip para compartir)`. Deja `Builds/BattleBots_Windows.zip` dentro del
proyecto (que está en OneDrive, así se sincroniza solo). Con Unity cerrado también se puede en batch:

```
"C:\Program Files\Unity\Hub\Editor\6000.3.9f1\Editor\Unity.exe" -batchmode -quit -projectPath "C:\Users\calij\OneDrive\Desktop\unity\My project" -executeMethod BattleBots.EditorTools.BattleBotsSetupWizard.BuildWindowsBatch -logFile "%TEMP%\battlebots_build.log"
```
