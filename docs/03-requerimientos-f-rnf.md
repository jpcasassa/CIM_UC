# 03 · Requerimientos funcionales y no funcionales

## Requerimientos funcionales (RF)

Prioridad: **Alta** = indispensable para el flujo principal; **Media** = mejora la experiencia del flujo; **Baja** = deseable si hay tiempo.

| ID | El sistema deberá | RA origen | Prioridad |
|---|---|---|---|
| RF-01 | Mostrar en Explorar un listado de contenidos con tipo, título y año, que incluya proyectos, capacidades I+D, integrantes, publicaciones y actividades. | RA-01 | Alta |
| RF-02 | Permitir acceder a cada uno de los 5 tipos de contenido desde Inicio y desde Explorar. | RA-01 | Alta |
| RF-03 | Permitir ingresar texto de búsqueda y mostrar los contenidos cuyo título o descripción coincidan, sin distinguir mayúsculas ni tildes. | RA-02 | Alta |
| RF-04 | Mostrar un mensaje de "sin resultados" con opción de limpiar la búsqueda cuando no existan coincidencias. | RA-02 | Media |
| RF-05 | Permitir filtrar el listado por tipo, área temática y año, y combinar los 3 filtros a la vez. | RA-03 | Alta |
| RF-06 | Mostrar los filtros activos y permitir quitarlos de forma individual o todos juntos. | RA-03 | Media |
| RF-07 | Mostrar la cantidad de resultados obtenidos tras una búsqueda o un filtro. | RA-03 | Baja |
| RF-08 | Mostrar en el detalle de un proyecto su título, descripción, año, estado y área temática. | RA-04 | Alta |
| RF-09 | Permitir volver desde el detalle al listado conservando la búsqueda y los filtros aplicados. | RA-04 | Media |
| RF-10 | Mostrar en la pantalla de contenidos relacionados los integrantes, capacidades y publicaciones asociados a un proyecto. | RA-05 | Alta |
| RF-11 | Permitir abrir el detalle de cualquier contenido relacionado desde la pantalla de contenidos relacionados. | RA-05 | Alta |
| RF-12 | Mostrar la organización a la que pertenece cada integrante relacionado. | RA-05 | Media |
| RF-13 | Listar actividades indicando su tipo (evento, formación u oportunidad de colaboración) y su fecha. | RA-06 | Alta |
| RF-14 | Permitir filtrar las actividades y oportunidades por área temática. | RA-06 | Media |
| RF-15 | Permitir ir desde el detalle de un proyecto a las actividades y oportunidades de su misma área temática. | RA-06 | Media |
| RF-16 | Mostrar un formulario de contacto con nombre, correo ficticio y mensaje, con el contenido referido precargado. | RA-07 | Alta |
| RF-17 | Validar antes de enviar que los 3 campos estén completos y que el correo tenga formato válido. | RA-07 | Alta |
| RF-18 | Registrar la solicitud simulada con su fecha y mostrar una confirmación con el resumen de lo enviado. | RA-07 | Alta |
| RF-19 | Permitir volver a Inicio desde la pantalla de confirmación. | RA-07 | Baja |

## Requerimientos no funcionales (RNF)

| ID | Requisito | Cómo se verifica |
|---|---|---|
| RNF-01 (Usabilidad) | Un usuario debe poder llegar desde Inicio al formulario de contacto en un máximo de 5 toques y completar el flujo principal completo en menos de 2 minutos. | Prueba con al menos 5 personas, cronometrando el flujo y contando los toques. |
| RNF-02 (Accesibilidad) | El texto debe tener un contraste mínimo de 4.5:1 con su fondo y un tamaño mínimo de 14 sp; los elementos táctiles deben medir al menos 48 × 48 dp. | Revisión con Accessibility Scanner en las 7 pantallas; 0 incumplimientos. |
| RNF-03 (Accesibilidad) | El 100 % de los íconos y botones sin texto debe tener descripción de contenido para lectores de pantalla. | Recorrido de las 7 pantallas con TalkBack activado. |
| RNF-04 (Rendimiento) | La búsqueda y los filtros deben mostrar resultados en menos de 1 segundo con un catálogo de hasta 50 registros; cada pantalla debe cargar en menos de 2 segundos. | Medición de tiempos en 10 repeticiones; el promedio debe cumplir los límites. |
| RNF-05 (Rendimiento) | La aplicación no debe cerrarse inesperadamente durante 20 recorridos consecutivos del flujo principal. | Ejecución de 20 recorridos con casos de prueba; 0 cierres. |
| RNF-06 (Compatibilidad Android vertical) | La aplicación debe funcionar en Android 8.0 (API 26) o superior, en orientación vertical y en pantallas de 360 × 640 dp hasta 412 × 915 dp, sin texto cortado ni elementos superpuestos. | Pruebas en al menos 2 dispositivos o emuladores con distinto tamaño de pantalla. |
| RNF-07 (Datos ficticios) | El 100 % de los datos debe ser ficticio, sintético, público o anonimizado, sin datos personales reales; el catálogo debe tener como mínimo 10 proyectos, 10 integrantes, 6 capacidades, 8 publicaciones y 6 actividades. | Revisión del conjunto de datos registro por registro y conteo por entidad. |
| RNF-08 (Consistencia visual) | Las 7 pantallas deben usar una sola paleta de colores, un máximo de 2 tipografías y espaciados múltiplos de 8 dp, con los mismos componentes para listas, botones y filtros. | Comparación de las pantallas implementadas con los mockups mediante una lista de chequeo. |
