## Problema y enfoque

CIM UC tiene mucha información como proyectos, capacidades I+D, integrantes, publicaciones y actividades, además lo revisan personas muy distintas. Desde el celular, alguien que busca algo puntual no tiene una forma fácil de encontrarlo ni de ver con qué otras cosas se relaciona. Nuestra idea es una app para Android, representado por un MVP con datos ficticios. Nos enfocamos en el flujo principal que incluye dos tipos de usuario, investigador/universidad y empresa/industria

## Alcance

El flujo que vamos a mostrar es: Inicio, Explorar con búsqueda y filtros, detalle de proyecto, contenidos relacionados, contacto simulado y confirmación.

Dejamos fuera el login real, las notificaciones y copiar el sitio web de CIM UC. Al ser un caso académico los excluimos del flujo que elegimos.

## Requerimientos de alto nivel

RA-01 La app deberá permitir explorar proyectos, capacidades I+D, integrantes, publicaciones y actividades de CIM UC.

RA-02 La app deberá permitir buscar contenidos escribiendo texto.

RA-03 La app deberá permitir filtrar contenidos por tipo, área temática y año.

RA-04 La app deberá permitir ver el detalle de un contenido.

RA-05 La app deberá permitir ver cómo se relacionan los contenidos, por ejemplo los integrantes, capacidades y publicaciones de un proyecto.

RA-06 La app deberá permitir encontrar actividades y oportunidades de colaboración según lo que le interese a la persona.

RA-07 La app deberá permitir enviar una solicitud de contacto simulada a CIM UC y ver una confirmación.

## Pantallas

P-01: Inicio.

P-02: Explorar (listado, búsqueda y filtros).

P-03: Detalle de proyecto.

P-04: Contenidos relacionados.

P-05: Actividades y oportunidades de colaboración.

P-06: Formulario de contacto simulado.

P-07: Confirmación.

## Entidades

Proyecto: id_proyecto, titulo, descripcion, anio, estado, id_area.

CapacidadID: id_capacidad, nombre, descripcion, id_area.

Publicacion: id_publicacion, titulo, anio, tipo, resumen, id_area.

Integrante: id_integrante, nombre, rol, especialidad, id_organizacion.

Organizacion: id_organizacion, nombre, tipo, descripcion.

Actividad: id_actividad, titulo, tipo (evento, formación u oportunidad de colaboración), fecha, descripcion, id_area.

AreaTematica: id_area, nombre, descripcion.

SolicitudContacto: id_solicitud, nombre_contacto, correo_ficticio, mensaje, fecha, id_contenido_referido.

---

**Las relaciones entre proyectos e integrantes, capacidades y publicaciones son de muchos a muchos, así que en el modelo de datos se incluyen tablas intermedias.**