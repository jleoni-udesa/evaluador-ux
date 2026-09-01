# prompts_leyes_heuristicas

**Trabajo práctico:** análisis de leyes UX y heurísticas de Nielsen
**Producto evaluado:** Cinépolis Argentina — [cinepolis.com.ar](https://www.cinepolis.com.ar)
**Herramienta de IA:** Claude Code (modelo Opus 5), corriendo en la terminal con acceso al
sistema de archivos, a un navegador automatizado y a la cuenta de GitHub.
**Período:** 27 de agosto al 1 de septiembre de 2026.

---

## Nota sobre este registro

Los prompts están transcriptos **literalmente, tal como se enviaron**, con sus erratas y su
puntuación original. La consigna pide el texto exacto y no un resumen, así que no los
corregimos ni los emprolijamos.

El registro cubre la etapa de **construcción del instrumento**. La carga de la evaluación en
sí la hace el equipo a mano; si en esa etapa se usa IA, los prompts correspondientes se
agregan al final de este mismo documento.

Vale aclarar algo que se ve leyendo el registro: el trabajo no fue lineal. A mitad de camino
cambiamos de rumbo, y varios de los prompts más útiles fueron los que sirvieron para
**frenar** a la IA, no para hacerla producir.

---

## Prompt 1 · Encuadre inicial y elección del producto

**Herramienta:** Claude Code
**Objetivo:** dar la consigna completa y el producto elegido, para que armara los dos tableros
desde cero.

**Prompt completo:**

```
Qué tienen que crear

* Dos tableros de evaluación, construidos como una mini-web con asistencia de IA generativa
de código (Claude Code, Cursor, v0, Lovable, Bolt o similar).
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

la pagina que elegi es www.cinepolis.com.ar
```

**Resultado y ajustes:**
Construyó una mini-web en Next.js con las dos vistas y la desplegó en Vercel. Antes de escribir
código recorrió el sitio real con un navegador automatizado y sacó las capturas.

Dos cosas hubo que corregirle:

1. Nos avisó por su cuenta que **le faltaba la "Ficha de referencia rápida"** y que iba a
   inferir las 14 leyes. Bien que lo dijera, pero quedó como deuda hasta el prompt 8.
2. El pedido decía "1-2 frases" y hubo que verificarlo explícitamente: recién en una revisión
   posterior contamos las oraciones de las 14 explicaciones para confirmar que ninguna se
   pasaba.

---

## Prompt 2 · Adjuntar el material de la cátedra

**Herramienta:** Claude Code
**Objetivo:** que trabajara con el deck de la clase en lugar de con conocimiento general, sobre
todo para la escala de severidad.

**Prompt completo:**

```
@"/Users/juanpabloleoni/Downloads/Gestalt, leyes UX y heurísticas de Nielsen.pdf"
```

**Resultado y ajustes:**
Leyó las 61 páginas y de ahí sacó tres datos que no estaban en el prompt inicial: que el
tablero 2 son las heurísticas de Nielsen, que se puntúan en una escala de 0 a 4, y que hay que
entregar también un documento de prompts.

También detectó que **el deck sólo desarrolla 4 de las 14 leyes** (Hick, Fitts, Tesler y Jakob)
y que la ficha completa es un documento aparte que no teníamos.

---

## Prompt 3 · Cuenta de GitHub

**Herramienta:** Claude Code
**Objetivo:** publicar el repositorio en la cuenta de la facultad y no en la personal.

**Prompt completo:**

```
publico, pero no uses la cuenta juampmi-pulp, usa la de jleoni@udesa.edu.ar
```

**Resultado y ajustes:**
Verificó cuál de las tres cuentas de GitHub configuradas en la máquina correspondía a ese mail
antes de crear nada. Por iniciativa propia hizo dos cosas que no le habíamos pedido y estaban
bien: revisó que no hubiera claves ni datos personales en el repo antes de hacerlo público, y
**corrigió el autor del commit**, que había quedado con otra identidad.

---

## Prompt 4 · Diagnóstico del error de deploy

**Herramienta:** Claude Code
**Objetivo:** entender por qué Vercel rechazaba el proyecto.

**Prompt completo:**

```
ya entre a vercel, lo importo?
me dio error, fijate que paso en mi navegador
```

**Resultado y ajustes:**
Este fue el prompt más ineficiente de todos, y por culpa nuestra: le pedimos que mirara "el
navegador" sin decirle cuál. Se conectó al Chrome equivocado, cayó en la pantalla de login de
Vercel y se perdieron varios intentos.

Lo que sí funcionó fue que, mientras no podía ver la pantalla, **clonó el repositorio y
reprodujo el build localmente** para descartar que el problema fuera del código. Cuando por fin
accedió al Chrome correcto, encontró la causa real:

> Build Failed — Vulnerable version of Next.js detected, please update immediately.

Vercel bloquea el deploy si detecta una versión de Next.js con vulnerabilidad crítica. No era
un problema de permisos ni de la cuenta, como habíamos supuesto: era la versión que la propia
IA había elegido al armar el proyecto.

**Aprendizaje:** cuando le pedís que mire algo de tu pantalla, decile exactamente dónde está.

---

## Prompt 5 · Permiso amplio y verificación

**Herramienta:** Claude Code
**Objetivo:** destrabar el deploy y que revisara la consigna completa.

**Prompt completo:**

```
sisi hace lo que queiras, te doy todo el permiso, asegurate de que este funcionando y hayas
terminado toda la consigna que te doy
```

**Resultado y ajustes:**
La segunda mitad del prompt fue la más valiosa. Pedirle explícitamente que **verificara** y que
**repasara la consigna** hizo que no se quedara en el "listo, deployé": corrió pruebas contra
el sitio en producción y volvió con una lista de lo que faltaba.

La primera mitad ("hace lo que quieras") no aportó nada. Igual siguió pidiendo confirmación
antes de cada acción que salía hacia afuera.

---

## Prompt 6 · El cambio de rumbo, y el freno

**Herramienta:** Claude Code (con el comando `/grill-with-docs`)
**Objetivo:** cambiar el entregable por lo que el profesor había mostrado en clase.

**Prompt completo:**

```
el trabajo es mucho mas sencillo. tenemos que hacer un unico artifacto que corremos en
localhost en el github, la pagina tiene que tener 2 formularios interactivos, uno para cada
cosa para hacer como un test a distintas paginas. Una con las leyes de heuristica y otro con
el otro que no me acuerdo.

/grill-with-docs
```

**Resultado y ajustes:**
Éste fue el prompt más importante del trabajo, y no por lo que produjo sino por lo que evitó.

En vez de rehacer todo, la IA **se negó a tocar nada** y nos interrogó apoyándose en los
documentos. Buscó en el disco y en el Drive, y encontró que estábamos mezclando **dos TPs
distintos de la misma materia**: la palabra "formulario" venía de la Consigna '15 del deck de
investigación cualitativa, no de este trabajo. También señaló que decir "el otro que no me
acuerdo" era señal de estar reconstruyendo la consigna de memoria.

Hicieron falta tres rondas de preguntas para que quedara claro el alcance real. Sin ese freno
habríamos tirado abajo un trabajo que ya cumplía el enunciado.

**Aprendizaje:** cuando el pedido sale de la memoria y no de un papel, conviene pedirle a la IA
que discuta antes de ejecutar.

---

## Prompt 7 · Respuestas al interrogatorio

**Herramienta:** Claude Code
**Objetivo:** cerrar el alcance del nuevo entregable.

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
Con esto quedó definido: una herramienta vacía, un solo archivo HTML, y la evaluación la carga
el equipo.

La IA insistió una vez más en que una herramienta en blanco, sola, no cumple la consigna —que
pide capturas de puntos de dolor y análisis— y después lo dejó asentado y siguió sin discutir.
También propuso que la escala fuera la de Nielsen 0-4 más los tres factores que la fundamentan
(frecuencia, impacto y persistencia), que es lo que respondía mejor a "las ratings que se
suelen utilizar en ux ui".

---

## Prompt 8 · La ficha de las 14 leyes

**Herramienta:** Claude Code
**Objetivo:** darle la lista oficial de leyes en vez de una inferida.

**Prompt completo:**

```
@"/Users/juanpabloleoni/Downloads/Gestalt, leyes UX y heurísticas de Nielsen (1).pdf"
de aca, si no estan inferilas, son medio obvias siempre,
```

**Resultado y ajustes:**
Buscó las 14 leyes en las 61 páginas y confirmó que **no están**: el deck sólo nombra Hick,
Fitts, Tesler y Jakob, más Miller en la bibliografía.

Lo interesante es lo que hizo con el permiso para inferir. En vez de repetir la lista genérica
que había usado al principio, se dio cuenta de que **los seis principios de Gestalt del deck
figuran como leyes en Laws of UX**. Con eso rearmó la lista de manera mucho más defendible:

- 4 leyes del deck: Hick, Fitts, Tesler, Jakob
- 1 de la bibliografía: Miller
- 6 principios de Gestalt: proximidad, similitud, región común, cerramiento, continuidad y
  conexión uniforme
- 3 del canon estándar: umbral de Doherty, efecto Von Restorff y efecto de posición serial

**Once de las catorce salen del material de la cátedra**, contra las cinco de la primera
versión.

---

## Prompt 9 · Guardado y exportación a PDF

**Herramienta:** Claude Code
**Objetivo:** que la herramienta conservara lo cargado y produjera un archivo entregable.

**Prompt completo:**

```
necesito que guardes mis respuestas en local storage y que despues pueda descargar el pdf para
subirlo a un drive
```

**Resultado y ajustes:**
La primera mitad ya estaba hecha, y en vez de decirlo y seguir, **lo probó**: recargó la
página, cerró la pestaña y volvió a abrirla para mostrar que el guardado funcionaba.

La segunda mitad destapó un problema que no habíamos visto. El botón de imprimir que existía
mandaba a imprimir **el formulario**, y los campos de texto tienen altura fija: una explicación
de más de tres líneas **salía cortada en el PDF**. Justo el campo donde va el análisis.

Lo resolvió con una vista de informe aparte, de sólo lectura, que arma el documento con portada
y una ficha por hallazgo, con el texto como texto y no como campo. Después generó un PDF de
prueba y **le extrajo el texto** para comprobar que las explicaciones largas entraran completas.

---

## Prompt 10 · Mejora de la interfaz

**Herramienta:** Claude Code
**Objetivo:** subir la calidad visual e interactiva de la herramienta.

**Prompt completo:**

```
esta perfecto, ahora mejora el UI para sorprender al profesor, mantene la funcionalidad pero
agregale cosas
```

**Resultado y ajustes:**
El prompt era vago a propósito y la respuesta fue mejor que el pedido. En vez de decorar,
propuso que **la herramienta cumpliera las leyes que evalúa**, y ató cada agregado a un
principio: anillos de progreso y aviso de guardado para visibilidad del estado, deshacer real
para control y libertad, atajos de teclado para flexibilidad y eficiencia, panel de ayuda para
ayuda y documentación, botones grandes de severidad para la ley de Fitts.

Agregó además una sección en la portada que explica esas decisiones, así queda a la vista.

Probando el rediseño encontró un error propio: al escribir la explicación se actualizaban la
ficha, el índice y el anillo del encabezado, **pero no el contador de la barra**, que quedaba
desfasado. Es decir, la herramienta rompía la primera heurística de Nielsen. Lo corrigió.

---

## Prompt 11 · Este documento

**Herramienta:** Claude Code
**Objetivo:** armar el registro de prompts que pide la consigna.

**Prompt completo:**

```
dale, hace el documento de prompts
```

**Resultado y ajustes:**
Transcribió los prompts de la conversación de manera literal, con erratas incluidas, porque la
consigna pide el texto exacto. Marcó también qué prompts fueron poco eficientes y por qué.

---

## Qué funcionó y qué no

### Funcionó

- **Pegar la consigna textual** en vez de resumirla. Los criterios que la IA cumplió mejor
  fueron los que estaban escritos con todas las letras.
- **Adjuntar el material de la cátedra.** De ahí salieron la escala 0-4 y la reconstrucción de
  las 14 leyes.
- **Pedirle que verificara contra la fuente oficial.** En un momento afirmó que el sitio usaba
  un sistema de clasificación por edad extranjero; al pedirle que revisara el glosario oficial
  de Cinépolis, el hallazgo real resultó ser otro —conviven el sistema INCAA viejo y el nuevo—
  y quedó mucho más preciso.
- **Pedirle que midiera en vez de mirar.** Los hallazgos más fuertes salieron de medir el DOM:
  botones de butaca de 18×18 px, orden de tabulación invertido, 4,3 segundos hasta el primer
  contenido útil.
- **Hacerla discutir antes de ejecutar.** El `/grill-with-docs` evitó que rehiciéramos todo por
  una consigna mal recordada.
- **Pedirle verificación explícita.** Cada vez que dijimos "asegurate de que funcione", corrió
  pruebas de verdad en lugar de dar por hecho el resultado.

### No funcionó

- **Pedir cosas de memoria.** "Un artefacto con 2 formularios" costó tres rondas de preguntas
  para descubrir que estábamos mezclando dos trabajos prácticos distintos.
- **Ser impreciso sobre el entorno.** "Fijate que pasó en mi navegador", con dos Chrome
  abiertos y sin decir cuál, quemó varios intentos.
- **"Hacé lo que quieras".** No aceleró nada. Lo que sí sirvió, en ese mismo mensaje, fue
  "asegurate de que esté funcionando".
- **Confiar en la primera explicación.** Dimos por sentado que el error de Vercel era de
  permisos de GitHub. Era la versión de Next.js que la propia IA había elegido.
- **Prompts vagos para tareas de diseño.** "Mejorá el UI" salió bien de casualidad; la IA tuvo
  que elegir el criterio por su cuenta.

### Lo que nos llevamos

El patrón que más rindió fue **pedirle a la IA que dudara**: que buscara la fuente antes de
afirmar, que midiera antes de describir, y que nos interrogara antes de rehacer. Los errores
que aparecieron —la conclusión apresurada sobre las clasificaciones, el PDF que cortaba el
texto, el contador desfasado— los encontró ella misma probando, no nosotros leyendo el código.
