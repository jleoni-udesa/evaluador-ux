# Evaluador UX

Herramienta de evaluación heurística de interfaces. Se aplica a cualquier app o sitio web
y produce dos tableros:

- **Leyes UX** — las 14 leyes como checklist, marcando en cada punto si el producto cumple o rompe.
- **Heurísticas de Nielsen** — las 10 completas, puntuadas en la escala de severidad 0-4.

## Cómo se usa

Es **un solo archivo**. No hace falta instalar ni levantar nada:

```
abrí index.html con doble clic
```

También funciona desplegado: es HTML estático, se sube a cualquier hosting tal cual.

## Qué hace

- Carga del producto evaluado: nombre, URL, equipo y fecha.
- Por cada ley: cumple / rompe / no aplica, pantalla donde se observa, captura y explicación,
  con contador de caracteres para no pasarse de las 1-2 frases.
- Por cada heurística: severidad 0-4, los tres factores de Nielsen que la fundamentan
  (frecuencia, impacto y persistencia), captura, y la explicación separada en qué pasa,
  por qué rompe o cumple, y qué impacto tiene en la persona usuaria.
- Capturas por arrastre o clic. Se redimensionan a 1600 px y se convierten a JPEG antes de
  guardarse, porque el almacenamiento del navegador tiene un techo de ~5 MB y un screenshot
  de pantalla completa se lo consume solo.
- Guardado automático en el navegador, con aviso visible de que quedó guardado.
- **Índice lateral** con un punto por criterio que cambia según el avance: sin empezar,
  empezado, o completo (y en las leyes, del color de cumple/rompe/no aplica).
- **Anillos de progreso** en la barra superior, siempre a la vista.
- **Atajos de teclado**: `0`–`4` para severidad, `C`/`R`/`N` para cumple/rompe/no aplica,
  `J`/`K` para recorrer fichas, `/` para buscar, `G` seguido de `I`/`L`/`H`/`P` para navegar,
  y `?` para la ayuda. No se disparan mientras se escribe en un campo.
- **Deshacer** en las acciones destructivas: quitar una captura, vaciar todo o importar
  encima se revierte durante siete segundos.
- **Buscador** y filtros por estado o severidad.
- **Tema** claro, oscuro o el del sistema.
- **Exportar / importar JSON**, para repartir el trabajo entre el equipo y unirlo después.
- **Descargar PDF**: una vista de informe aparte, de sólo lectura, que arma el documento final
  con portada, resumen y todas las fichas cargadas. Se imprime desde ahí eligiendo
  «Guardar como PDF» en el diálogo del navegador. El informe avisa antes si falta alguna
  heurística o si no se llegó al piso de 8 leyes, y ese aviso no sale impreso.
- Resumen de severidad con el promedio y la distribución.

Nada se envía a ningún servidor: todo vive en el navegador de quien evalúa.

## Escala de severidad

| | |
|---|---|
| 0 | No es un problema — se cumple la heurística |
| 1 | Cosmético — no hace falta arreglarlo salvo que sobre tiempo |
| 2 | Menor — conviene resolverlo, con prioridad baja |
| 3 | Mayor — es importante, hay que resolverlo |
| 4 | Catástrofe — imperativo resolverlo antes de publicar |

## Las 14 leyes

Once salen directamente del material de la cátedra: las cuatro leyes que el deck desarrolla
(Hick, Fitts, Tesler, Jakob), Miller, y los seis principios de Gestalt que en Laws of UX
figuran como leyes (proximidad, similitud, región común, cerramiento, continuidad y conexión
uniforme). Las tres restantes son las más estándar del canon: umbral de Doherty,
efecto Von Restorff y efecto de posición serial.

Si la Ficha de referencia rápida de la cátedra trae otra lista, se edita el array `LEYES`
al principio del `<script>` en `index.html` y la herramienta se rearma sola.
