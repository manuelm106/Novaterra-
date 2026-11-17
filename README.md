# Novaterra

## Guía Vecinal (`guia-vecinal/index.html`)

Directorio vecinal construido a partir del chat de WhatsApp de la ciudadela.

- **Importar chat**: sube el `.txt` (o `.zip`) que genera WhatsApp en *Más → Exportar chat → Sin archivos*.
  El chat se procesa en el navegador; detecta teléfonos recomendados (formato Ecuador 09…, +593…)
  y respuestas que se repiten (horarios de buses, etc.), los agrupa y los clasifica por categoría.
  Solo se guardan los textos que el usuario marca, sin nombres ni números de quien escribió.
- **Directorio**: búsqueda, categorías y orden por calificación o por cantidad de vecinos que lo recomendaron.
- **Reseñas**: cada vecino da de 1 a 5 estrellas y un comentario (una reseña por persona y recomendación).

La página está publicada como Artifact de claude.ai y usa su base de datos compartida (`db`) y la identidad del visitante (`user`).
