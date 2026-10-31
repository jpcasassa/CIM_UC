# 06 · Mockups: especificación por pantalla

**Convenciones comunes:**
- **Barra inferior:** 3 destinos (Inicio, Explorar, Actividades), visible solo en P-01, P-02 y P-05.
- **Barra superior con flecha de retroceso:** en P-03, P-04 y P-06.
- **Medidas:** elementos táctiles de al menos 48 × 48 dp, texto de al menos 14 sp, orientación vertical (RNF-02, RNF-06).
- **Consistencia:** las tarjetas, los botones y las etiquetas de filtro usan los mismos componentes en todas las pantallas (RNF-08).

## P-01 · Inicio

**Objetivo:** dar acceso directo a cada tipo de contenido para que la persona llegue a lo que busca en un toque.

**Componentes (de arriba a abajo):**
1. Barra superior con el nombre "CIM UC".
2. Texto breve de bienvenida que explica que la app permite explorar proyectos, capacidades y actividades.
3. Campo de búsqueda (al tocarlo abre P-02 con el teclado activo).
4. Cinco tarjetas de acceso, una por tipo: Proyectos, Capacidades I+D, Integrantes, Publicaciones y Actividades, cada una con su cantidad de registros.
5. Barra inferior (Inicio, Explorar, Actividades).

**Acciones → destino:**
- Toca el campo de búsqueda → P-02
- Toca "Proyectos", "Capacidades I+D", "Integrantes" o "Publicaciones" → P-02, con ese tipo ya seleccionado
- Toca "Actividades" → P-05
- Toca "Explorar" en la barra inferior → P-02
- Toca "Actividades" en la barra inferior → P-05

**HU que cubre:** HU-01

**Datos del modelo:** cantidad de registros de Proyecto, CapacidadID, Integrante, Publicacion y Actividad.

## P-02 · Explorar

**Objetivo:** listar contenidos y permitir acotarlos con búsqueda por texto y filtros.

**Componentes (de arriba a abajo):**
1. Barra superior con el título "Explorar".
2. Campo de búsqueda con botón para borrar el texto.
3. Fila de etiquetas de tipo: Proyectos, Capacidades I+D, Integrantes, Publicaciones y Actividades.
4. Selectores de área temática y de año.
5. Etiquetas de filtros activos, cada una con una "x", y el botón "Limpiar todo".
6. Contador de resultados (por ejemplo, "12 resultados").
7. Lista de tarjetas, cada una con tipo, título y año.
8. Estado vacío: mensaje "Sin resultados" y botón "Limpiar búsqueda".
9. Barra inferior.

**Acciones → destino:**
- Escribe en el buscador → P-02, con la lista filtrada por texto
- Cambia el tipo, el área o el año → P-02, con la lista filtrada
- Toca la "x" de una etiqueta o "Limpiar todo" → P-02, con la lista actualizada
- Toca una tarjeta → P-03
- Toca "Inicio" o "Actividades" en la barra inferior → P-01 o P-05

**HU que cubre:** HU-01, HU-02, HU-03

**Datos del modelo:**
- Proyecto: titulo, descripcion, anio
- CapacidadID: nombre, descripcion
- Integrante: nombre, especialidad
- Publicacion: titulo, anio, resumen
- Actividad: titulo, descripcion, fecha
- AreaTematica: nombre (opciones del filtro)

## P-03 · Detalle de proyecto

**Objetivo:** mostrar la información clave de un proyecto y servir de punto de partida hacia sus relaciones, sus actividades y el contacto.

**Componentes (de arriba a abajo):**
1. Barra superior con flecha de retroceso y el título "Proyecto".
2. Título del proyecto.
3. Fila de datos: año, estado (etiqueta) y área temática (etiqueta).
4. Descripción del proyecto.
5. Botón "Ver contenidos relacionados".
6. Botón "Ver actividades de esta área".
7. Botón fijo inferior "Contactar a CIM UC".

**Acciones → destino:**
- Toca la flecha de retroceso → P-02, con búsqueda y filtros conservados
- Toca "Ver contenidos relacionados" → P-04
- Toca "Ver actividades de esta área" → P-05, con esa área preseleccionada
- Toca "Contactar a CIM UC" → P-06, con este proyecto como contenido referido

**HU que cubre:** HU-04, HU-06

**Datos del modelo:** Proyecto (titulo, descripcion, anio, estado) y AreaTematica (nombre, obtenida por id_area).

**Variante para otros tipos:** al abrir una capacidad, un integrante, una publicación o una actividad desde P-02 o P-04, esta misma pantalla muestra el detalle de ese contenido, con su título y sus atributos en lugar de los del proyecto, y sin los botones de relacionados ni de contacto.

## P-04 · Contenidos relacionados

**Objetivo:** mostrar cómo se conecta un proyecto con sus integrantes, capacidades y publicaciones.

**Componentes (de arriba a abajo):**
1. Barra superior con flecha de retroceso y el título "Relacionados".
2. Título del proyecto de origen como subtítulo.
3. Sección "Integrantes": lista con nombre, rol y organización.
4. Sección "Capacidades I+D": lista con el nombre de cada capacidad.
5. Sección "Publicaciones": lista con título, año y tipo.
6. Mensaje "Sin elementos asociados" en las secciones vacías.
7. Botón fijo inferior "Contactar a CIM UC".

**Acciones → destino:**
- Toca la flecha de retroceso → P-03 (el proyecto de origen)
- Toca un integrante, una capacidad o una publicación → P-03 (variante del tipo tocado)
- Toca "Contactar a CIM UC" → P-06, con el proyecto de origen como contenido referido

**HU que cubre:** HU-05

**Datos del modelo:**
- Proyecto: titulo
- Proyecto_Integrante e Integrante: nombre, rol
- Organizacion: nombre (obtenida por id_organizacion)
- Proyecto_Capacidad y CapacidadID: nombre
- Proyecto_Publicacion y Publicacion: titulo, anio, tipo

## P-05 · Actividades y oportunidades de colaboración

**Objetivo:** mostrar eventos, formación y oportunidades de colaboración, filtrables por área de interés.

**Componentes (de arriba a abajo):**
1. Barra superior con el título "Actividades".
2. Selector de área temática (etiquetas, con la opción "Todas").
3. Lista de tarjetas de actividad, cada una con título, tipo (evento, formación u oportunidad de colaboración), fecha y descripción breve.
4. Mensaje "Sin actividades en esta área" cuando la lista queda vacía.
5. Barra inferior.

**Acciones → destino:**
- Elige un área → P-05, con la lista filtrada
- Toca "Inicio" o "Explorar" en la barra inferior → P-01 o P-02
- Usa el retroceso del sistema si llegó desde un proyecto → P-03

**HU que cubre:** HU-06, HU-07

**Datos del modelo:** Actividad (titulo, tipo, fecha, descripcion) y AreaTematica (nombre, como opciones del filtro).

## P-06 · Formulario de contacto simulado

**Objetivo:** permitir enviar una solicitud de contacto ficticia que ya indique el proyecto de origen y validar los datos antes de enviarla.

**Componentes (de arriba a abajo):**
1. Barra superior con flecha de retroceso y el título "Contactar a CIM UC".
2. Tarjeta "Contenido referido" con el título del proyecto (solo lectura).
3. Campo "Nombre".
4. Campo "Correo" (ficticio).
5. Campo "Mensaje" (varias líneas).
6. Mensaje de error bajo cada campo con problema.
7. Botón "Enviar solicitud".

**Acciones → destino:**
- Toca "Enviar solicitud" con los 3 campos completos y el correo válido → P-07, con la solicitud registrada con la fecha del día
- Toca "Enviar solicitud" con un campo vacío o un correo inválido → P-06, con los errores marcados y los datos ya escritos conservados
- Toca la flecha de retroceso → P-03 o P-04 (la pantalla desde la que llegó)

**HU que cubre:** HU-08, HU-09

**Datos del modelo:** Proyecto (titulo, por id_contenido_referido) y SolicitudContacto (nombre_contacto, correo_ficticio, mensaje).

## P-07 · Confirmación

**Objetivo:** dar certeza de que la solicitud simulada quedó registrada y devolver a la persona al flujo de exploración.

**Componentes (de arriba a abajo):**
1. Ícono de confirmación.
2. Título "Solicitud enviada".
3. Resumen: nombre, contenido referido, mensaje y fecha.
4. Botón "Volver a Inicio".

**Acciones → destino:**
- Toca "Volver a Inicio" → P-01
- Usa el retroceso del sistema → P-01 (para no volver al formulario y reenviar)

**HU que cubre:** HU-10

**Datos del modelo:** SolicitudContacto (nombre_contacto, mensaje, fecha) y Proyecto (titulo, por id_contenido_referido).
