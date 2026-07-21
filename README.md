# Resultados de oposiciones de Educarm

Esta aplicación consulta las publicaciones de los tribunales de Educarm, genera tablas de resultados por especialidad e integra también la lista de interinos.

> **Aviso:** esta web no es una fuente oficial. Los datos oficiales deben consultarse siempre en la [página de la Consejería de Educación](https://servicios.educarm.es/admin/index2.php?aplicacion=PUBLICACIONES_TRIBUNALES&module=publicacionesTribunales&anyo=2026&convocatoria=OPOPRI26).

## Cómo funciona

1. Se consultan periódicamente las publicaciones disponibles para cada especialidad y tribunal.
2. Se descargan los PDF de la primera prueba, segunda prueba y baremación.
3. Los candidatos se identifican usando especialidad, tribunal, número de orden e ID anonimizado. Para el baremo, cuyo PDF no incluye número de orden, se comprueban también el nombre y el ID anonimizado.
4. Solo se publican candidatos que han superado la primera prueba.
5. Se generan archivos CSV y HTML con buscador y ordenación de columnas.
6. Las listas de interinos se leen de sus CSV y se publican como una clasificación independiente para cada especialidad.

## Notas y baremo

- **1ª Prueba (Total):** resultado conjunto de las partes A y B.
- **Nota final (examen):** media de la primera y segunda prueba, cuando ambas han sido superadas.
- **Baremo (tribunal):** puntuación de méritos publicada oficialmente por el tribunal.
- **Nota final (con Baremo):** `Nota final (examen) × 0,6666 + Baremo (tribunal) × 0,3333`.
- **Posición:** se calcula usando la nota final con baremo oficial. Cada especialidad tiene dos clasificaciones independientes: acceso 1 y acceso 2 (reserva para personas con discapacidad). Un aspirante solo se compara con quienes pertenecen a su misma especialidad y acceso. Si todavía no hay posición numérica, la tabla indica el motivo exacto: suspenso, no presentado, pendiente de calificar o pendiente de baremo.

## Resumen del índice

La portada muestra el total de candidatos que superaron la primera prueba y, para cada especialidad, cuántos han aprobado o suspendido la segunda prueba, no se han presentado, siguen pendientes de calificar o están pendientes de baremación. Las filas con el texto «No Presentado» se registran como `NP`. La publicación del baremo también confirma que el tribunal ha cerrado la segunda prueba; si un aspirante no figura en sus documentos de calificaciones, deja de considerarse pendiente y se registra como no presentado. Un tribunal se considera pendiente de baremar únicamente cuando tiene aspirantes que han superado las dos pruebas y todavía no ha publicado su documento único de baremación. Los suspensos no se incluyen en este cálculo.

## Lista de interinos

Cada ficha de especialidad permite alternar entre los resultados de la oposición y la lista de interinos correspondiente. Esta lista procede de la lista provisional BI y muestra puesto, nombre, DNI anonimizado y puntuación total. Es una clasificación independiente de las notas y posiciones de la oposición.

El listado conjunto es la unión de las listas de especialidad después de aplicar una exclusión global por plaza. Si una persona obtiene plaza en cualquier especialidad, se elimina por completo de la lista general y de todas las listas de especialidad en las que figuraba. Las personas restantes aparecen una sola vez en la lista general, ordenadas de mayor a menor por puntuación total, y su fila indica todas sus especialidades.

Las cifras del índice se interpretan así:

- **Candidatos en la lista general:** número de personas distintas. Cada persona se cuenta una sola vez.
- **Apariciones en listas de especialidad:** suma de las veces que esas personas aparecen en las distintas especialidades. Por ejemplo, una persona incluida en AL, PT y PRI cuenta como una candidata y como tres apariciones.
- **Exclusiones por plaza:** apariciones retiradas de las listas porque la persona ha obtenido plaza en alguna especialidad. No equivale necesariamente al mismo número de personas distintas: si una persona con plaza figuraba en AL, PT y PRI, se contabilizan tres apariciones eliminadas.

Antes de generar las listas se identifican globalmente las personas que han obtenido plaza y se eliminan de todas las especialidades. Los cupos de acceso 1 y acceso 2 se aplican como máximos independientes: si un acceso tiene menos aprobados que plazas, solo se excluyen los aprobados reales y las plazas sobrantes no eliminan a otras personas. Después se recalculan correlativamente los puestos de cada lista de interinos, conservando también el puesto original para facilitar la comparación.

## Archivos generados

- `index.html`: portada con enlaces a todas las especialidades.
- `all_specialties.html`: resultados conjuntos.
- `<ESPECIALIDAD>.html`: resultados de una especialidad.
- `interinos.html`: índice general de la lista de interinos.
- `interinos_todas.html`: listado conjunto de interinos de todas las especialidades.
- `interinos_<ESPECIALIDAD>.html`: lista de interinos de una especialidad.
- Los archivos `.csv` contienen los mismos resultados y los campos internos utilizados durante el procesamiento.

La web se adapta a móviles y permite buscar y ordenar candidatos directamente en el navegador.
