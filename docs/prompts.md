Con el documento de replanteamiento y el contexto del caso, escribe un doc en markdown "01-replanteamiento-caso" sin introduccion  y con las siguientes secciones: 
Problema, Usuarios afectados, Propósito, Alcance actual, Fuera de alcance (cada ítem con motivo en una línea)

Con el documento de replanteamiento, escribe 02-requerimientos-alto-nivel: usa sus RA, cada uno como "La aplicación deberá permitir". Tabla debe verse de esta manera:
RA -> problema que resuelve.

Escribe 03-requerimientos-f-rnf
RF, tabla con ID | "El sistema deberá" | RA origen | prioridad. Cada RA del documento de replanteamiento debe tener mas de 1 RF

min 6 RNF (usabilidad, accesibilidad, rendimiento, compatibilidad Android vertical, datos ficticios, consistencia visual), tabla con ID | requisito | cómo se verifica. 
Los requisitos tienen que contar con cifras segun corresponda

Escribe 04-casos-uso-o-historias: 8 a 10 historias.
 Cada una: HU-NUMERO | "Como  quiero  para" | 2-3 criterios de aceptación observables | RF. Deben cubrir todo el flujo y ambos perfiles. Tabla final HU → RF → P-NUMERO. Sin historias genéricas


Escribe 05-modelo-datos: erDiagram en Mermaid con las entidades, atributos y sus tipos, PK/FK, cardinalidades. Debe incluir Proyecto–Integrante, Proyecto–CapacidadID y Proyecto–Publicacion (muchos a muchos con tabla intermedia).
 Debajo, por entidad: atributo | tipo | descripción | RF que lo exige.
 
Escribe 06-mockups como especificación por pantalla P-01 a P-07: objetivo | componentes de arriba a abajo | acciones → pantalla destino | HU que cubre | datos del modelo que muestra. Agrega flowchart Mermaid de navegación. Una pantalla por bloque

Audita los 6 archivos. Responde con una lista de hallazgos, cada uno como: archivo | ID | problema | corrección.
Busca: RA sin RF, RF sin HU, HU sin pantalla, entidad sin RF, pantalla con datos que no existen en el modelo, contradicciones. Si no hay faltas, escribe OK