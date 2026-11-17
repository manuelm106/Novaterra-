# Novaterra · Guía Vecinal

Directorio vecinal construido a partir del chat de WhatsApp de la ciudadela:
contactos recomendados (plomeros, almuerzos, gas…) y respuestas repetidas (horarios de buses…),
con estrellas y reseñas de los vecinos.

| Carpeta | Qué es |
|---|---|
| `web/` | **Versión pública** (Firebase). Cualquiera la abre y califica sin crear cuenta. |
| `guia-vecinal/` | Versión Artifact de claude.ai (requiere cuenta de claude.ai). |
| `firestore.rules` | Reglas de seguridad de la base de datos. |
| `firebase.json` | Configuración para publicar con Firebase Hosting. |

## Cómo funciona la versión pública

- **Vecinos**: abren el enlace y entran de forma anónima automáticamente (sin registro).
  Pueden buscar, calificar con 1–5 estrellas, dejar una reseña y agregar recomendaciones.
  Cada dispositivo deja una sola reseña por recomendación.
- **Administradores** (tú): entran con Google desde el pie de página. Solo ellos pueden
  importar el chat, editar o borrar cualquier ficha y moderar reseñas.
- El chat exportado se procesa en el navegador; solo se guardan los textos que el
  administrador marca, sin nombres ni números de quien escribió.

## Puesta en marcha (≈15 minutos, gratis)

### 1. Crear el proyecto de Firebase
1. Entra a <https://console.firebase.google.com> con tu cuenta de Google → **Agregar proyecto**
   (por ejemplo `guia-novaterra`). Google Analytics no es necesario.
2. **Compilación → Firestore Database → Crear base de datos** → modo *producción* →
   ubicación cercana (p. ej. `southamerica-east1` o `us-east1`).
3. **Compilación → Authentication → Comenzar → Método de acceso**, activa:
   - **Anónimo**
   - **Google**

### 2. Conectar la página
1. **Configuración del proyecto (⚙️) → Tus apps → ícono Web `</>`** → registra la app
   (marca también *Firebase Hosting*).
2. Copia el objeto `firebaseConfig` que te muestra y pégalo en `web/firebase-config.js`.
   Esos datos no son secretos; la seguridad la dan las reglas.

### 3. Publicar las reglas de seguridad
En **Firestore Database → Reglas**, reemplaza todo por el contenido de `firestore.rules` y pulsa **Publicar**.
(O con la herramienta de línea de comandos: `firebase deploy --only firestore:rules`.)

### 4. Publicar la página
Opción A — Firebase Hosting (recomendado, queda en `https://<proyecto>.web.app`):
```bash
npm install -g firebase-tools
firebase login
firebase use --add          # elige tu proyecto
firebase deploy             # publica web/ y las reglas
```
Opción B — sin instalar nada: arrastra la carpeta `web/` a <https://app.netlify.com/drop>.
Luego agrega el dominio que te den (p. ej. `xxxx.netlify.app`) en
**Authentication → Configuración → Dominios autorizados**.

### 5. Hacerte administrador
1. Abre tu página, baja al pie y pulsa **Entrar con Google**.
2. La página te muestra tu ID de usuario con un botón **Copiar**.
3. En **Firestore Database → Datos → Iniciar colección**: ID de colección `admins`,
   ID de documento = tu ID copiado, agrega un campo cualquiera (p. ej. `nombre: "Manuel"`) y guarda.
4. Recarga la página: aparece la pestaña **Importar chat**.

### 6. Importar el chat
En WhatsApp: grupo → **Más → Exportar chat → Sin archivos**. Sube el `.txt` o `.zip`
en la pestaña **Importar chat**, revisa lo encontrado y pulsa **Guardar en la guía**.
Puedes repetirlo cada cierto tiempo con un chat más nuevo: las fichas existentes se actualizan, no se duplican.

Comparte el enlace en el grupo de WhatsApp y listo.

## Límites del plan gratuito (Spark)
50.000 lecturas y 20.000 escrituras al día, 1 GiB de datos: de sobra para una ciudadela.
Como los vecinos entran sin cuenta, alguien podría calificar varias veces usando otro
navegador o modo incógnito; los administradores pueden borrar fichas y reseñas abusivas.
