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
| 1. El coordinador abre el detalle del proyecto y selecciona Gestionar etapas.|El sistema muestra la lista de etapas  |                                                                                        
| 2. El coordinador elige Agregar, Editar o Eliminar.| Opciones del menú (Agregar, Editar, Eliminar) y formularios correspondientes a cada opción. |
| 3. El sistema despliega formulario con nombre, responsable, estado, fechas estimadas, observaciones.|  Formulario con campos: nombre, responsable, estado, fechas estimada, observaciones. |
| 4. El coordinador completa o modifica los campos y confirma.| El sistema le da la autorización a el cordinador para rellenar los campos |
| 5. El sistema valida (responsable válido, fechas coherentes, estado permitido).
| el sistema revisa los campos para ver si hay un error en alguno de ellos quietandole al coordinador permisos que le consedio en el anterior paso. |
| 6.El sistema guarda los cambios y registra el evento (alta/edición/baja). | El sistema guarda los cambios en una base de datos de proyectos.|
| 7.El servicio de notificaciones envía aviso al usuario responsable asignado afectado por la modificación.| El sistema le manda un aviso al sistema de notificaciones.|
| 8. El sistema actualiza la lista y muestra confirmación al coordinador.|El sistema recibe la notificación de que el usuario a recibido el mensaje por parte del sistema de notificaciónes  |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Que el proyecto exista y tenga etapas |
| **Poscondiciones:** | Etapas actualizadas |
| **Suposiciones:** | Que el sistema tenga los datos del proyecto |
| **Reunir requerimientos:** | Registro de proyectos, sistema de notificación , base de datos y un sistema para validar que no haya errores|
| **Aspectos sobresalientes:** | ¿Qué pasa si hay algún error por parte del coordinador ?¿Si el sistema  encuentra en la edición de proyecto un proyecto parecido? |
| **Prioridad:** | Tiempo  (Alta)  | 
| **Riesgo:** | Tiempo - Costo (Media - Alta) |
