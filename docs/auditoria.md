Feedback Claude:

Sin faltas (OK):

RA sin RF: OK. Cada RA tiene entre 2 y 4 RF.
RF sin HU: OK. Los 19 RF aparecen en alguna HU, con la observación del hallazgo 6.
HU sin pantalla: OK. Las 10 HU están en la tabla del 04 y coinciden con los bloques del 06.
Entidad sin RF: OK. Las 8 entidades y las 3 tablas intermedias tienen al menos un RF.

Hallazgos:

Archivo	ID	Problema	Corrección
05-modelo-datos (afecta 03 y 06)	RF-05, P-02	RF-05 y P-02 ofrecen filtrar por área y año en todos los tipos, pero Integrante no tiene id_area ni año, CapacidadID no tiene año y Actividad solo tiene fecha.	Agregar id_area a Integrante y anio a CapacidadID (el año de Actividad se deriva de fecha). Alternativa: acotar RF-05 y P-02 para que área y año se apliquen solo a los tipos que tienen ese atributo.
03-requerimientos-f-rnf (afecta 04 y 06)	RF-01, HU-01 crit. 3, P-02 comp. 7	Dicen que cada tarjeta muestra "tipo, título y año", pero CapacidadID e Integrante no tienen año ni titulo (tienen nombre), y Actividad usa fecha.	Reescribir como "tipo, título o nombre y, cuando exista, año o fecha".
03-requerimientos-f-rnf (afecta 04)	RF-03, HU-02 crit. 1	La búsqueda dice "título o descripción", pero Integrante tiene nombre y especialidad, Publicacion tiene resumen y CapacidadID tiene nombre.	Reescribir como "título o nombre, y descripción, resumen o especialidad".
06-mockups	P-03, flowchart	P-03 define que "atrás" va a P-02, pero su variante se abre también desde P-04, y ahí "atrás" debería volver a P-04. El flowchart solo tiene la arista P03 → P02.	Definir que "atrás" vuelve a la pantalla de origen (P-02 o P-04) y agregar al flowchart P03 -->|Atrás| P04.
06-mockups	P-02, P-05, RNF-08	El filtro de área es un selector en P-02 y etiquetas con "Todas" en P-05, lo que contradice RNF-08 (mismos componentes de filtro).	Usar el mismo componente en ambas pantallas.
04-casos-uso-o-historias	HU-03, RF-02	RF-02 exige acceder a los 5 tipos "desde Inicio y desde Explorar", pero solo HU-01 lo cubre y solo para Inicio. La elección de tipo en Explorar ocurre en HU-03, que no lo traza.	Agregar RF-02 a HU-03, en su ficha y en la tabla de trazabilidad.
05-modelo-datos	Organizacion.tipo, Organizacion.descripcion, AreaTematica.descripcion	Se asignan a RF-12 y RF-05, que solo piden mostrar el nombre de la organización y filtrar por área, y ninguna pantalla los muestra.	Mostrar tipo y descripcion de la organización en la variante de P-03 para integrantes y citar RF-11. Para AreaTematica.descripcion, quitarlo o marcarlo "sin RF".
03-requerimientos-f-rnf	RNF-07	El mínimo del catálogo no incluye Organizacion, AreaTematica ni las relaciones, que necesitan RF-12, RF-05 y P-04.	Agregar: al menos 4 organizaciones, 5 áreas y, por cada proyecto de demostración, al menos 2 integrantes, 1 capacidad y 1 publicación asociados.
01-replanteamiento-caso	Alcance actual	El flujo principal omite P-05, aunque RA-06 y la lista de pantallas de ese mismo documento lo incluyen.	Agregar "con ramal a Actividades y oportunidades (P-05) desde Inicio y desde el detalle de proyecto".
06-mockups (afecta 04)	P-07, HU-10 crit. 1, RF-18	RF-18 pide mostrar "el resumen de lo enviado", pero el resumen de P-07 omite correo_ficticio.	Incluir el correo en el resumen de P-07 y en el criterio 1 de HU-10, o ajustar RF-18 para que no diga "resumen completo".

Las cifras que propongo en el hallazgo 8 son mías, igual que las del RNF-07 original; ajústenlas si su catálogo real es distinto.