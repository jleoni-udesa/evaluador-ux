# prompts_leyes_heuristicas

**Trabajo práctico:** análisis de leyes UX y heurísticas de Nielsen
**Entregable:** herramienta de evaluación heurística — [evaluador-ux.vercel.app](https://evaluador-ux.vercel.app)
**Herramienta de IA:** Claude Code (modelo Opus 5), corriendo en la terminal con acceso al
sistema de archivos, a un navegador automatizado y a la cuenta de GitHub.
**Período:** 31 de agosto y 1 de septiembre de 2026.

---

## Nota sobre este registro

Los prompts están transcriptos **literalmente, tal como se enviaron**, con sus erratas y su
puntuación original. La consigna pide el texto exacto y no un resumen, así que no los
corregimos ni los emprolijamos.

El registro arranca en el momento en que replanteamos el trabajo. Los primeros intercambios los
hicimos sin tener la consigna escrita delante y trabajando sobre una idea aproximada de lo que
había que hacer; recién en el prompt 2 la pasamos completa, y de ahí en adelante todo se apoya
en el enunciado y no en lo que nos acordábamos.

Este documento cubre la **construcción del instrumento**. La carga de la evaluación la hace el
equipo a mano; si en esa etapa se usa IA, los prompts se agregan al final de este mismo
documento.

---

## Prompt 1 · Replantear qué había que construir

**Herramienta:** Claude Code (con el comando `/grill-with-docs`)
**Objetivo:** redefinir el entregable a partir de lo que el profesor había mostrado en clase, y
pedirle a la IA que discutiera el planteo antes de ejecutarlo.

**Prompt completo:**

```
el trabajo es mucho mas sencillo. tenemos que hacer un unico artifacto que corremos en
localhost en el github, la pagina tiene que tener 2 formularios interactivos, uno para cada
cosa para hacer como un test a distintas paginas. Una con las leyes de heuristica y otro con
el otro que no me acuerdo.

/grill-with-docs
```

**Resultado y ajustes:**
La IA **no escribió una sola línea de código** y en su lugar nos interrogó apoyándose en los
documentos que teníamos. Buscó en el disco y en el Drive y encontró que estábamos mezclando
**dos trabajos prácticos distintos de la misma materia**: la palabra "formulario" venía de la
Consigna '15 del deck de investigación cualitativa, no de éste. También marcó que decir "el
otro que no me acuerdo" era señal de que estábamos reconstruyendo el enunciado de memoria, y
que el segundo tablero eran las leyes UX.

Nos hizo cinco preguntas numeradas, con una recomendación por cada una, y avisó que no iba a
tocar nada hasta que las contestáramos.

**Aprendizaje:** cuando el pedido sale de la memoria y no de un papel, conviene pedirle a la IA
que discuta antes de producir.

---

## Prompt 2 · Pasarle la consigna completa

**Herramienta:** Claude Code
**Objetivo:** contestar el interrogatorio y, sobre todo, darle el enunciado textual para que
dejara de trabajar sobre suposiciones.

**Prompt completo:**

```
1. Me lo mostro el profesor, es tal como te lo describi, no es nada muy refinado
2. nono, son distinas tareas ahi te paso la consigna:

Algunas aclaraciones sobre la tarea de análisis de leyes y heurísticas.

Qué tienen que crear

* Dos tableros de evaluación, construidos como una mini-web con asistencia de IA generativa de
código  (Claude Code, Cursor, v0, Lovable, Bolt o similar).
* Puede ser un solo proyecto con dos vistas/secciones, o dos proyectos separados; en ambos
casos tienen que quedar desplegados en Vercel.
* Cada tablero funciona como un documento de evaluación navegable: por cada ley o heurística,
muestra el hallazgo, la evidencia (captura) y el análisis escrito. No hace falta funcionalidad
de backend (es contenido estático que ustedes completan con su análisis real).

Tablero 1: leyes UX

* Recorran las navegaciones principales de su producto usando las 14 leyes de la Ficha de
referencia rápida como checklist. No hace falta encontrar las 14 en el mismo producto:
prioricen las más evidentes.
* Sugerencia de cobertura mínima: documenten al menos 8 de las 14 leyes con evidencia real
(cumplida o rota). Es un piso orientativo, ajustable según lo que efectivamente encuentren en
su producto.

Por cada ley documentada, el tablero muestra:

* Ley UX: nombre de la ley (de las 14 de la Ficha de referencia).
* Cumple / rompe: indicar si el producto respeta la ley o la incumple en el punto analizado.
* Captura: screenshot del punto exacto de la interfaz donde se observa.
* Explicación: 1-2 frases que respondan la pregunta guía de esa ley: qué pasa y por qué.

Tablero 2: heurísticas de Nielsen
A diferencia de las leyes UX, acá evalúan las 10 heurísticas completas: es el estándar de una
evaluación heurística real.

Por cada heurística, el tablero muestra:

* Heurística: una de las 10 heurísticas de Nielsen (las 10, sin excepción).
* Severidad: escala de Nielsen 0-4: 0 no es un problema, 1 cosmético, 2 menor, 3 mayor, 4
catástrofe de usabilidad.
* Captura:  screenshot del punto de dolor (severidad ≥ 1) o del punto donde se cumple bien
(severidad 0).
* Explicación: qué pasa, por qué rompe o cumple la heurística, y qué impacto tiene en la
persona usuaria.

Documento de prompts ("prompts_leyes_heuristicas")
Se sube al Drive del equipo con ese nombre exacto. No es un anexo protocolar: nos interesa ver
cómo iteraron con la IA, qué funcionó y qué no. Por cada prompt relevante, tiene que incluir:

* Herramienta de IA usada: Claude Code, Cursor, v0, ChatGPT, etc.
* Objetivo del prompt: qué le pidieron a la IA y para qué parte del tablero.
* Prompt completo: el texto exacto, no un resumen.
* Resultado y ajustes: qué devolvió la IA y qué tuvieron que corregir o reformular.

Entregables

* Link al tablero (o los dos tableros) desplegado en Vercel.
* Link al repositorio en GitHub, público o compartido con el equipo docente.
* Documento "prompts_leyes_heuristicas" en el Drive del equipo.
* Fecha de entrega: miércoles 2 de septiembre.

3. local
```

**Resultado y ajustes:**
Éste fue el prompt más productivo de todos, y lo único que hicimos fue copiar y pegar el
enunciado. Con el texto a la vista, la IA detectó de entrada tres cosas que no estábamos
cumpliendo:

1. **Las etiquetas de severidad estaban mal.** La consigna dice `2 menor` y `3 mayor`; el deck
   de la clase dice "media prioridad" y "alta prioridad", y nos habíamos guiado por el deck.
2. **Faltaba el impacto en la persona usuaria.** La consigna pide que la explicación de cada
   heurística diga qué pasa, por qué, **y qué impacto tiene**. Ese tercer campo no estaba.
3. **El registro de prompts no servía como estaba**, porque la consigna pide el texto exacto de
   cada prompt y lo que teníamos era una narración parafraseada.

También marcó una contradicción entre nuestra respuesta 3 ("local") y el enunciado que
acabábamos de pegar, que pide el deploy en Vercel en dos lugares distintos.

**Aprendizaje:** pegar el enunciado textual vale más que cualquier explicación nuestra. Los
criterios que la IA cumplió mejor fueron los que estaban escritos con todas las letras.

---

## Prompt 3 · Cerrar el alcance

**Herramienta:** Claude Code
**Objetivo:** contestar las rondas siguientes del interrogatorio para definir qué construir.

**Prompt completo (segunda ronda):**

```
1. porque recien el profesor me dijo que local basta
2. era una landing page donde habia links para 2 como formularios para evaluar cada cosa, una
para las leyes de heuristica y el otro para el otro. Es como una herramienta para evaluar otras
apps/webapps en base al ui
3. si, y con las ratings que se suelen utilizar en ux ui, hay que evaluar para las leyes ux y
las heuristicas de nielsen
```

**Prompt completo (tercera ronda):**

```
1. No, despues la tenemos que hacer nostors a la evaluacion, vos me tenes que dar solo la
herramineta
2. un unico index.html
3. si, y con las ratings que se suelen utilizar en ux ui
```

**Resultado y ajustes:**
Con esto quedó definido el entregable: una herramienta de evaluación vacía, en un solo archivo
HTML, que el equipo completa después.

La IA dejó asentado una vez que una herramienta en blanco, sola, no cumple la consigna —que
pide capturas de puntos de dolor y análisis escrito— y después siguió sin volver sobre el tema.
Sobre "las ratings que se suelen utilizar en ux ui" propuso la escala de Nielsen 0-4 más los
tres factores que la fundamentan: **frecuencia, impacto y persistencia**, que es el estándar
real de una evaluación heurística.

También decidió por su cuenta no pisar el trabajo anterior y crear un repositorio nuevo, para
que un error no se llevara puesto lo que ya estaba andando.

---

## Prompt 4 · La ficha de las 14 leyes

**Herramienta:** Claude Code
**Objetivo:** darle la lista oficial de leyes en lugar de una inventada.

**Prompt completo:**

```
@"/Users/juanpabloleoni/Downloads/Gestalt, leyes UX y heurísticas de Nielsen (1).pdf"
de aca, si no estan inferilas, son medio obvias siempre,
```

**Resultado y ajustes:**
Buscó las 14 leyes en las 61 páginas del deck y confirmó que **no están**: sólo nombra Hick,
Fitts, Tesler y Jakob, más Miller en la bibliografía. La "Ficha de referencia rápida" que
menciona la consigna es un documento aparte que no teníamos.

Lo interesante fue lo que hizo con el permiso para inferir. En vez de tirar una lista genérica,
se dio cuenta de que **los seis principios de Gestalt que el deck enseña figuran como leyes en
Laws of UX**, y rearmó la lista sobre el material de la cátedra:

- 4 leyes que el deck desarrolla: Hick, Fitts, Tesler, Jakob
- 1 de la bibliografía: Miller
- 6 principios de Gestalt: proximidad, similitud, región común, cerramiento, continuidad y
  conexión uniforme
- 3 del canon estándar: umbral de Doherty, efecto Von Restorff y efecto de posición serial

**Once de las catorce salen del material que dio el profesor.** Dejó además la lista en un
único array al principio del archivo, para poder cambiarla si aparece la ficha.

---

## Prompt 5 · Guardado y exportación a PDF

**Herramienta:** Claude Code
**Objetivo:** que la herramienta conservara lo cargado y produjera un archivo entregable.

**Prompt completo:**

```
necesito que guardes mis respuestas en local storage y que despues pueda descargar el pdf para
subirlo a un drive
```

**Resultado y ajustes:**
La primera mitad ya estaba hecha, y en vez de decirlo y seguir de largo, **lo probó**: recargó
la página, cerró la pestaña y volvió a abrirla para mostrar que el guardado funcionaba de
verdad.

La segunda mitad destapó un problema que no habíamos visto. El botón de imprimir que existía
mandaba a imprimir **el formulario**, y los campos de texto tienen altura fija: una explicación
de más de tres líneas **salía cortada en el PDF**. Justo el campo donde va el análisis, y no lo
hubiéramos notado hasta abrir el archivo ya entregado.

Lo resolvió con una vista de informe aparte, de sólo lectura, que arma el documento con portada,
datos del proyecto, resumen de severidad y una ficha por hallazgo, con el texto como texto y no
como campo de formulario. Después generó un PDF de prueba y **le extrajo el texto** para
comprobar que las explicaciones largas entraran completas.

Agregó también un aviso que aparece antes de imprimir si faltan heurísticas o si no se llegó al
piso de 8 leyes, y que no sale en el impreso.

---

## Prompt 6 · Mejora de la interfaz

**Herramienta:** Claude Code
**Objetivo:** subir la calidad visual e interactiva de la herramienta.

**Prompt completo:**

```
esta perfecto, ahora mejora el UI para sorprender al profesor, mantene la funcionalidad pero
agregale cosas
```

**Resultado y ajustes:**
El prompt era vago a propósito y la respuesta fue mejor que el pedido. En lugar de decorar,
propuso que **la herramienta cumpliera las leyes que evalúa**, y ató cada agregado a un
principio concreto:

| Agregado | Principio |
|---|---|
| Anillos de progreso, aviso de guardado, índice con punto de avance | Visibilidad del estado del sistema |
| Deshacer real al quitar captura, vaciar o importar | Control y libertad del usuario |
| Enunciado y pregunta guía siempre a la vista mientras se escribe | Reconocer antes que recordar |
| Atajos de teclado, inhibidos mientras se escribe en un campo | Flexibilidad y eficiencia de uso |
| Panel de ayuda con `?` | Ayuda y documentación |
| Botones de severidad como bloques amplios, no radios diminutos | Ley de Fitts |

Sumó además una sección en la portada que explica esas decisiones, así el criterio queda a la
vista y no hay que deducirlo.

Probando el rediseño encontró un error propio: al escribir la explicación se actualizaban la
ficha, el índice y el anillo del encabezado, **pero no el contador de la barra**, que quedaba
desfasado. Dicho de otro modo, la herramienta rompía la primera heurística de Nielsen. Lo
corrigió y unificó los cuatro lugares en una sola función.

---

## Prompt 7 · Este documento

**Herramienta:** Claude Code
**Objetivo:** armar el registro de prompts, y después ajustarlo.

**Prompt completo (primero):**

```
dale, hace el documento de prompts
```

**Prompt completo (ajustes):**

```
hacelo apartir del prompt 6
```

```
sacale eso de cambio de rumbo, antes no habia entendido la consigna, deja dessde ese mensaje,
despues poner cuando te paso la consigna
```

**Resultado y ajustes:**
La primera versión abarcaba toda la conversación y encuadraba el prompt 1 como un "cambio de
rumbo". Eso estaba mal contado: no habíamos cambiado de rumbo, todavía no teníamos bien
entendida la consigna. Le pedimos recortar el registro y corregir el encuadre, y además sumar
el mensaje donde le pasamos el enunciado completo, que en la primera versión faltaba y era
justamente el más importante.

Al pedirle el recorte avisó que el prompt 1 empieza con "el trabajo es mucho más sencillo" y
que sin contexto no se entiende más sencillo que qué, y propuso resolverlo con una nota inicial
en vez de traer los intercambios anteriores.

---

## Qué funcionó y qué no

### Funcionó

- **Pegar el enunciado textual.** Fue el prompt más productivo de todos y lo único que hicimos
  fue copiar y pegar. De ahí salieron tres correcciones que no habíamos visto: las etiquetas de
  severidad, el campo de impacto en la persona usuaria, y el formato de este mismo documento.
- **Hacerla discutir antes de producir.** El `/grill-with-docs` evitó que construyéramos sobre
  una consigna mal recordada, y detectó que estábamos mezclando dos trabajos prácticos.
- **Adjuntar el material de la cátedra.** De ahí salió la reconstrucción de las 14 leyes con
  once tomadas del deck en vez de una lista genérica.
- **Pedirle que probara en vez de afirmar.** Cuando dijimos "guardá en local storage", en lugar
  de responder que ya estaba, recargó, cerró la pestaña y lo demostró. Y cuando armó el PDF, le
  extrajo el texto para verificar que nada quedara cortado.
- **Dejarla elegir el criterio en tareas abiertas.** "Mejorá el UI" derivó en una idea mejor que
  la que teníamos: que la herramienta aplique los principios que mide.

### No funcionó

- **Pedir cosas de memoria.** El primer prompt de este registro describía el trabajo de memoria
  y costó tres rondas de preguntas descubrir que mezclaba dos consignas distintas. Con el
  enunciado a mano, se habría resuelto en un mensaje.
- **Dar instrucciones que contradicen el enunciado.** Contestamos "local" en el mismo mensaje en
  el que pegábamos una consigna que pide Vercel en dos lugares. La IA lo marcó, pero es tiempo
  perdido.
- **Prompts vagos para tareas de diseño.** "Mejorá el UI para sorprender al profesor" salió bien,
  pero porque la IA eligió un criterio por su cuenta. Podría haber salido cualquier cosa.

### Lo que nos llevamos

Lo que más rindió fue **darle la fuente y pedirle que dude**: pegar el enunciado en vez de
resumirlo, adjuntar el material en vez de describirlo, y pedirle que verifique en vez de que
afirme. Los tres errores que aparecieron —las etiquetas de severidad mal, el PDF que cortaba el
texto y el contador desfasado— los encontró ella misma comparando contra la consigna o probando
lo que había construido, no nosotros leyendo el código.
