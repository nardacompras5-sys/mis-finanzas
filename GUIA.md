# Mis Finanzas · Guía para tener tu app propia

Tu app funciona sin Claude. Tus datos viven en tu celular/compu y en una carpeta privada de **tu** Google Drive que solo esta app puede ver. Hazlo una sola vez, desde una computadora (20–30 min).

## 1. Publica la app en GitHub Pages (gratis)
1. Entra a https://github.com y crea una cuenta.
2. Arriba a la derecha: **+ → New repository**. Nombre: `mis-finanzas`. Déjalo **Public** y toca **Create repository**.
3. Toca **uploading an existing file** y arrastra los archivos de esta carpeta: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`. Toca **Commit changes**.
4. Ve a **Settings → Pages**. En *Branch* elige `main` y `/ (root)` → **Save**.
5. Espera 1–2 minutos. Tu app estará en: `https://TU-USUARIO.github.io/mis-finanzas/`

> El código es público, pero **tus datos no**: nunca se suben a GitHub, solo a tu Drive.

## 2. Crea tu proyecto en Google Cloud
1. Entra a https://console.cloud.google.com con tu correo de Google y acepta los términos.
2. Arriba, **Seleccionar proyecto → Proyecto nuevo**. Nombre: `Mis Finanzas` → **Crear**. Asegúrate de que quede seleccionado.

## 3. Activa Google Drive
1. Menú ☰ → **APIs y servicios → Biblioteca**.
2. Busca **Google Drive API** → ábrela → **Habilitar**.

## 4. Configura la pantalla de inicio de sesión
1. Menú ☰ → **Google Auth Platform** (o *APIs y servicios → Pantalla de consentimiento de OAuth*) → **Comenzar**.
2. Nombre de la app: `Mis Finanzas`. Correo de asistencia: tu correo. Siguiente.
3. Público: **Externo**. Siguiente. Contacto: tu correo. Acepta y **Crear**.
4. Ve a **Público → Usuarios de prueba → Add users** y agrega **tu correo**. Guarda.

## 5. Crea tu "ID de cliente"
1. **Google Auth Platform → Clientes → Crear cliente**.
2. Tipo: **Aplicación web**. Nombre: `Mis Finanzas`.
3. En **Orígenes de JavaScript autorizados → Agregar URI** escribe: `https://TU-USUARIO.github.io` (sin `/mis-finanzas` y sin barra al final).
4. **Crear** y copia el **ID de cliente** (termina en `.apps.googleusercontent.com`).
5. *(Opcional, recomendado)* En GitHub abre `index.html` → lápiz ✏️ → busca `DEFAULT_CLIENT_ID = ''` y pega tu ID entre las comillas → **Commit**. Así no tendrás que pegarlo en cada dispositivo.

## 6. Entra con tu correo
1. Abre `https://TU-USUARIO.github.io/mis-finanzas/`.
2. Toca **Conectar** (o la etiqueta de arriba, junto a tu nombre) → pega el ID si te lo pide → **Entrar con Google**.
3. Elige tu cuenta. Google dirá *"Google no verificó esta app"*: es normal porque es **tu** app → **Continuar** → permite el acceso.
4. Arriba verás **☁️ En tu Drive**.

## 7. Pasa tus datos desde la app de Claude
1. En la app de Claude: **⚙️ Ajustes → 💾 Descargar copia de seguridad**.
2. En tu app nueva: **⚙️ Ajustes → ♻️ Restaurar / importar copia** → elige ese archivo → escribe la contraseña del candado → **Restaurar**.
3. Cuando confirmes que todo está, en la app de Claude puedes ir a **Ajustes → Borrar todos mis datos**.

## 8. Instálala como app
- **Android (Chrome):** menú ⋮ → **Instalar app** o **Agregar a la pantalla principal**.
- **iPhone (Safari):** botón Compartir → **Agregar a inicio**. *(Si en iPhone el ingreso con Google falla desde el ícono, úsala desde Safari.)*
- En cada dispositivo nuevo: ábrela y toca **Entrar con Google** una vez.

## Bueno saber
- Funciona **sin internet**: guarda en el dispositivo y sube a tu Drive cuando vuelvas a tener conexión.
- La sesión de Google dura una hora y se renueva sola; a veces te pedirá **Volver a entrar**: es un toque.
- Si Google te pide entrar seguido, en **Google Auth Platform → Público** toca **Publicar app** (la app solo pide acceso a su propia carpeta, no necesita revisión).
- Haz una **copia de seguridad** de vez en cuando (Ajustes → 💾).
- Para actualizar la app en el futuro: reemplaza `index.html` en GitHub.
