# Resultados de oposiciones de Educarm

Esta aplicación consulta las publicaciones de los tribunales de Educarm y genera tablas de resultados por especialidad y una tabla conjunta.

> **Aviso:** esta web no es una fuente oficial. Los datos oficiales deben consultarse siempre en la [página de la Consejería de Educación](https://servicios.educarm.es/admin/index2.php?aplicacion=PUBLICACIONES_TRIBUNALES&module=publicacionesTribunales&anyo=2026&convocatoria=OPOPRI26).

## Cómo funciona

1. Se consultan periódicamente las publicaciones disponibles para cada especialidad y tribunal.
2. Se descargan los PDF de la primera prueba, segunda prueba y baremación.
3. Los candidatos se identifican usando especialidad, tribunal, número de orden e ID anonimizado. Para el baremo, cuyo PDF no incluye número de orden, se comprueban también el nombre y el ID anonimizado.
4. Solo se publican candidatos que han superado la primera prueba.
5. Se generan archivos CSV y HTML con buscador y ordenación de columnas.

## Notas y baremo

- **1ª Prueba (Total):** resultado conjunto de las partes A y B.
- **Nota final (examen):** media de la primera y segunda prueba, cuando ambas han sido superadas.
- **Baremo:** puntuación de méritos publicada por el tribunal.
- **Nota final (con Baremo):** `Nota final (examen) × 0,6666 + Baremo × 0,3333`.
- **Posición:** se calcula usando la nota final con baremo. Permanece vacía mientras el tribunal no haya publicado el baremo del candidato.

## Archivos generados

- `index.html`: portada con enlaces a todas las especialidades.
- `all_specialties.html`: resultados conjuntos.
- `<ESPECIALIDAD>.html`: resultados de una especialidad.
- Los archivos `.csv` contienen los mismos resultados y los campos internos utilizados durante el procesamiento.

La web se adapta a móviles y permite buscar y ordenar candidatos directamente en el navegador.
