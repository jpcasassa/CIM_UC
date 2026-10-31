# 04 · Historias de usuario

Perfiles: **Investigador** = investigador/universidad · **Empresa** = empresa/industria.

## HU-01 · Llegar a publicaciones desde Inicio (Investigador)

**Historia:** Como investigadora de otra universidad, quiero ver en Inicio un acceso directo a cada tipo de contenido, para llegar a las publicaciones de mi línea de trabajo sin recorrer menús.

**Criterios de aceptación:**
1. Inicio muestra 5 accesos: proyectos, capacidades I+D, integrantes, publicaciones y actividades.
2. Al tocar "Publicaciones", se abre Explorar mostrando solo publicaciones, en un único toque.
3. Explorar lista cada contenido con su tipo, título y año.

**RF:** RF-01, RF-02

## HU-02 · Buscar un tema técnico por texto (Empresa)

**Historia:** Como jefe de innovación de una empresa constructora, quiero buscar escribiendo "madera contralaminada", para encontrar rápido qué proyectos o capacidades de CIM UC tratan ese tema.

**Criterios de aceptación:**
1. Al escribir, la lista muestra solo contenidos cuyo título o descripción contienen el texto, sin importar mayúsculas ni tildes.
2. Sobre la lista aparece la cantidad de resultados encontrados.
3. Si no hay coincidencias, se muestra "sin resultados" con un botón para limpiar la búsqueda.

**RF:** RF-03, RF-04, RF-07

## HU-03 · Filtrar publicaciones recientes de un área (Investigador)

**Historia:** Como investigador en estructuras de madera, quiero combinar los filtros de tipo, área temática y año, para ver solo las publicaciones recientes de mi área.

**Criterios de aceptación:**
1. Al elegir tipo "Publicación", un área temática y un año, la lista se reduce a los contenidos que cumplen los 3 filtros.
2. Cada filtro aplicado aparece como una etiqueta sobre la lista.
3. Al quitar una etiqueta, la lista se actualiza sin afectar los otros filtros; un botón "Limpiar todo" quita los 3.

**RF:** RF-05, RF-06

## HU-04 · Revisar el estado de un proyecto antes de contactar (Empresa)

**Historia:** Como encargado de desarrollo de una empresa, quiero abrir el detalle de un proyecto y ver su año, estado y área, para saber si está en curso o finalizado antes de escribir a CIM UC.

**Criterios de aceptación:**
1. El detalle muestra título, descripción, año, estado y área temática del proyecto.
2. Al volver al listado, se mantienen el texto de búsqueda y los filtros que estaban aplicados.

**RF:** RF-08, RF-09

## HU-05 · Ver quién participa en un proyecto y qué ha publicado (Investigador)

**Historia:** Como investigadora que busca colaboradores, quiero ver los integrantes, capacidades y publicaciones de un proyecto, para identificar con quién contactar y qué trabajo previo respalda al equipo.

**Criterios de aceptación:**
1. La pantalla de contenidos relacionados muestra 3 secciones: integrantes, capacidades y publicaciones del proyecto.
2. Cada integrante aparece con el nombre de su organización.
3. Al tocar cualquier elemento relacionado, se abre su detalle.

**RF:** RF-10, RF-11, RF-12

## HU-06 · Pasar de un proyecto a oportunidades de colaboración (Empresa)

**Historia:** Como empresa interesada en un proyecto de secado de madera, quiero ir desde su detalle a las actividades y oportunidades de su misma área, para ver de qué formas puedo colaborar con CIM UC.

**Criterios de aceptación:**
1. El detalle del proyecto tiene un botón que abre las actividades de su misma área temática.
2. Cada actividad muestra su tipo (evento, formación u oportunidad de colaboración) y su fecha.

**RF:** RF-13, RF-15

## HU-07 · Acotar actividades a mi área de interés (Investigador)

**Historia:** Como investigador, quiero filtrar las actividades y oportunidades por área temática, para ver solo los eventos y programas de formación de mi campo.

**Criterios de aceptación:**
1. Al elegir un área temática, la lista muestra únicamente las actividades de esa área.
2. Cada actividad mantiene visibles su tipo y su fecha después de filtrar.

**RF:** RF-13, RF-14

## HU-08 · Enviar una solicitud que ya indique el proyecto visto (Empresa)

**Historia:** Como representante de una empresa, quiero que el formulario de contacto ya indique el proyecto que estaba viendo, para no tener que explicar a qué contenido me refiero.

**Criterios de aceptación:**
1. El formulario se abre con el título del proyecto de origen visible como contenido referido.
2. El formulario tiene 3 campos para completar: nombre, correo ficticio y mensaje.

**RF:** RF-16

## HU-09 · Corregir errores del formulario sin perder lo escrito (Investigador)

**Historia:** Como investigador, quiero que el formulario me indique qué campo falta o está mal, para corregirlo sin volver a escribir todo.

**Criterios de aceptación:**
1. Al enviar con un campo vacío, ese campo se marca con un mensaje de error y la solicitud no se envía.
2. Un correo sin "@" o sin dominio muestra un mensaje de error de formato.
3. Los datos ya escritos se mantienen mientras se corrigen los errores.

**RF:** RF-17

## HU-10 · Confirmar el envío y seguir explorando (Empresa)

**Historia:** Como representante de empresa, quiero ver una confirmación con el resumen de mi solicitud y volver a Inicio, para tener certeza de que quedó enviada y seguir revisando otros proyectos.

**Criterios de aceptación:**
1. Tras enviar, aparece la confirmación con el nombre, el contenido referido, el mensaje y la fecha de la solicitud.
2. Un botón "Volver a Inicio" lleva a Inicio en un solo toque.

**RF:** RF-18, RF-19

## Trazabilidad HU → RF → Pantalla

| HU | RF | Pantalla |
|---|---|---|
| HU-01 | RF-01, RF-02 | P-01 Inicio, P-02 Explorar |
| HU-02 | RF-03, RF-04, RF-07 | P-02 Explorar |
| HU-03 | RF-05, RF-06 | P-02 Explorar |
| HU-04 | RF-08, RF-09 | P-03 Detalle de proyecto |
| HU-05 | RF-10, RF-11, RF-12 | P-04 Contenidos relacionados |
| HU-06 | RF-13, RF-15 | P-03 Detalle de proyecto, P-05 Actividades y oportunidades |
| HU-07 | RF-13, RF-14 | P-05 Actividades y oportunidades |
| HU-08 | RF-16 | P-06 Formulario de contacto |
| HU-09 | RF-17 | P-06 Formulario de contacto |
| HU-10 | RF-18, RF-19 | P-07 Confirmación |
