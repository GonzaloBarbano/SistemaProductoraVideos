| **Nombre del escenario:**|Flujo principal -Gestionar Etapas de un Proyecto (Exitoso)  | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Gestión de etapas   | | **ID Única:** | 2 |
| **Área** |Sistema de Gestión de Etapas y proyectos | | |
| **Actor(es):** |  Coordinador, Usuario responsable, servicio de notificaciones.  | | | |
| **Descripción:** | Agregar, editar o eliminar etapas de un proyecto.| | | |

| **Activar Evento:** | Al administrador le llega la notificación de un proyecto nuevo  | **Identificadores e iniciadores de caso de uso** |
|---|---|---|
| **Tipo de señal:** | ☐ Externa | ☑️ Temporal | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El coordinador abre el detalle del proyecto y selecciona Gestionar etapas.|Lista de etapas asociadas al proyecto.  |                                                                                        
| 2. El coordinador elige Agregar, Editar o Eliminar.| Opciones de gestión: Agregar, Editar, Eliminar. |
| 3. El sistema despliega formulario con nombre, responsable, estado, fechas estimadas, observaciones.|  Formulario Etapa con campos: nombre, responsable, estado, fechas estimadas, observaciones. |
| 4. El coordinador completa o modifica los campos y confirma.| Datos de la etapa cargados o modificados en el formulario. |
| 5. El sistema valida (responsable válido, fechas coherentes, estado permitido).| Reglas de validación: existencia de responsable válido, coherencia de fechas, estados permitidos. |
| 6.El sistema guarda los cambios y registra el evento (alta/edición/baja). | Registro actualizado en la base de datos + evento de auditoría.|
| 7.El servicio de notificaciones envía aviso al usuario responsable asignado afectado por la modificación.| Notificación enviada al usuario responsable.|
| 8. El sistema actualiza la lista y muestra confirmación al coordinador.|Lista de etapas actualizada y mensaje de confirmación.  |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Que el proyecto exista y tenga etapas |
| **Poscondiciones:** | Etapas actualizadas |
| **Suposiciones:** | Que el sistema tenga los datos del proyecto |
| **Reunir requerimientos:** | Registro de proyectos, sistema de notificación , base de datos y un sistema para validar que no haya errores|
| **Aspectos sobresalientes:** | ¿Qué pasa si hay algún error por parte del coordinador ?¿Si el sistema  encuentra en la edición de proyecto un proyecto parecido? |
| **Prioridad:** | Tiempo  (Alta)  | 
| **Riesgo:** | Tiempo - Costo (Media - Alta) |
