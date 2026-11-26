# Primera Vista

Entrenador de lectura musical para piano.

## Ejercicios

Genera partituras a dos manos al azar, de 8 a 64 compases.

- Nivel de dificultad (1 Inicial a 5 Experto): ajusta figuras, acordes, registro, saltos, compases, alteraciones y tempo.
- Grupos y tresillos (tresillo de corcheas o negras, quintillo de semicorcheas, combinaciones de semicorcheas), síncopas y alteraciones accidentales.
- Uno o varios compases: cada ejercicio nuevo usa uno distinto.
- Conteo opcional (1 e & a, 1 & a, trip-let) sobre la partitura.
- Reglas para que se pueda tocar: acordes de una octava como máximo, saltos cortos tras notas rápidas y manos que no se cruzan.

- Figuras rítmicas por mano (redonda a semicorchea, con puntillo) y silencios opcionales.
- Acordes por mano: activar o no, 2, 3, 4 notas o mixto, y frecuencia (a veces, a menudo, siempre).
- Tonalidades: elige una o varias (mayores y menores hasta 6 alteraciones), o todas al azar. Cada clic en Nuevo ejercicio usa una de ellas, en orden aleatorio y sin repetir hasta pasar por todas.
- Registro y salto máximo de la melodía.
- Botón Tocar con metrónomo, cuenta previa y cursor que sigue el pulso. Toca un compás para empezar desde ahí.

Las partituras se dibujan con VexFlow 4.2.3, cargado desde jsDelivr.

## Técnica

Ejercicios cortos generados en las tonalidades elegidas: escalas, arpegios, trinos, bajo Alberti, cadencias con números romanos, inversiones y cinco dedos. Se eligen manos, figura (negras, corcheas, tresillos, semicorcheas o quintillos), octavas, progresión y repeticiones.

## Repertorio

Fragmentos al azar (4 u 8 compases, u obra completa) de arreglos simplificados de obras de dominio público: Petzold/Bach, Beethoven, Mozart, Bach, Pachelbel y Satie.

## Modo libre y modo examen

En Lectura, Técnica y Repertorio: el modo libre reproduce con cursor sin puntuar; el modo examen exige un teclado MIDI por USB, escucha lo que tocas al ritmo del metrónomo, marca cada nota en verde, naranja o rojo y da la puntuación final.

## Progreso

Racha de días cumpliendo la meta diaria, minutos de práctica (últimos 28 días), precisión de los exámenes, puntos débiles (tonalidades, figuras, manos, notas) con práctica sugerida y sesiones recientes. Todo se guarda solo en el navegador.

## Mis obras

Sube un archivo MIDI (.mid) y la app:

- Lo convierte en partitura: tonalidad (de la armadura del MIDI o estimada), compás, tempo, manos por pista (o separadas por el hueco más grande / Do central si hay una sola pista), notas cuantizadas a semicorcheas, ligaduras al cruzar barras o pulsos. Notación simplificada: una voz por mano.
- Analiza cada compás: notas por pulso, saltos tras notas rápidas, acordes amplios, pasajes rápidos, alteraciones y diferencias de ritmo entre manos, con un mapa de dificultad.
- Encuentra la estructura (bloques de 4 compases idénticos o transportados) y propone un plan compacto: un paso por sección difícil o media (con botones para cada mano, bloques de 1 o 2 compases y la escalera de tempo 60 → 75 → 90 → 100 %), un paso para las secciones fáciles, otro para las uniones y otro para la obra completa.
- Practica cualquier pasaje en bucle, con una mano sola (la otra suena de acompañamiento) y en modo examen con el teclado MIDI; los resultados van a Progreso.
- Ajustes de la partitura para recalcularla: ritmo en semicorcheas o simplificado a corcheas, cómo separar las manos (pistas, altura o un punto de división), intercambiar manos, compás y tonalidad forzados, y desplazar el inicio (anacrusa). Modo edición para cambiar la figura de cualquier nota o convertirla en silencio, con deshacer.
- Progreso por sección: cada examen guarda la precisión por compás; el plan y la estructura muestran barras con la última precisión y el tempo alcanzado, y cuántos compases están dominados.
- Exporta la partitura en PDF (A4).

Las obras y los pasos hechos del plan se sincronizan con tu cuenta dentro de claude.ai. En `ejemplos/` hay dos MIDI de prueba.

## Sonido y digitación

- Sonido de piano con muestras del SoundFont FluidR3 (licencia MIT, ver `piano/LICENSE.txt`). Si no cargan, se usa un sintetizador. Las muestras se cargan por `fetch`, así que `index.html` necesita servirse por HTTP (por ejemplo GitHub Pages) para oír el piano.
- Casilla "Digitación": en las escalas de Técnica usa la digitación estándar; en el resto, una propuesta calculada (programación dinámica sobre aperturas cómodas entre dedos, paso del pulgar y teclas negras).

## Sincronización

Dentro de claude.ai, la app guarda tu progreso y tus ajustes en tu espacio privado de la nube del artifact (capacidades `db` y `user`): `data/users/<id>/profile` para estadísticas y ajustes, y `data/users/<id>/profile/log/<AAAA-MM>` para el historial de sesiones por mes. El navegador mantiene una copia local, así que funciona sin conexión y se sincroniza al volver. Fuera de claude.ai (por ejemplo, abriendo `index.html`) solo guarda en el dispositivo; la capa de guardado está en un solo sitio para poder conectarla después a Firebase.

## Notas sueltas

Muestra una nota en el pentagrama (clave de Sol, de Fa o ambas) y la respondes con los botones de nombres, el teclado en pantalla, el teclado del ordenador o un piano digital por MIDI.

- Registro básico o con líneas adicionales, sostenidos y bemoles opcionales.
- Nombres Do Re Mi o C D E.
- Modo libre y contrarreloj de 60 segundos con récord.
- Repite más las notas que fallas o que tardas en leer (historial guardado en el navegador).

Abre `index.html` en el navegador. Para usar un piano MIDI, ábrelo en Chrome o Edge.
