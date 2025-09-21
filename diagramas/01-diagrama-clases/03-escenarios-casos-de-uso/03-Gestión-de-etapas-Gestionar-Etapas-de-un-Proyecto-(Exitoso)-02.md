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
| 1. El coordinador abre el detalle del proyecto y selecciona Gestionar etapas.
 |El sistema muestra la lista de etapas  |                                                                                                                                        
| 2. El coordinador elige Agregar, Editar o Eliminar.| El sistema espera a que el coordinador elija alguna de las opciones.Para mostrarle un formulario específico (Para cada elección) |
| 3. El sistema despliega formulario con nombre, responsable, estado, fechas estimadas, observaciones.| El usuario mira el formulario y el sistema espera las respuestas |
| 4. El coordinador completa o modifica los campos y confirma.| El sistema espera que el usuario rellene los campos |
| 5. El sistema valida (responsable válido, fechas coherentes, estado permitido).
| El usuario espera , mientras el sistema revisa los campos para ver si hay un error en alguno de ellos. |
| 6.El sistema guarda los cambios y registra el evento (alta/edición/baja). | El sistema guarda los cambios en una base de datos y le muestra al usuario un mensaje informando lo de esto|
| 7.El servicio de notificaciones envía aviso al usuario responsable asignado afectado por la modificación.| El sistema le manda un aviso al sistema de notificaciones para que notifique al usuario responsable  |
| 8. El sistema actualiza la lista y muestra confirmación al coordinador.|El sistema recibe la notificación de que el usuario a recibido el mensaje y se lo muestra al coordinador  |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Que el proyecto exista y tenga etapas |
| **Poscondiciones:** | Etapas actualizadas |
| **Suposiciones:** | Que el sistema tenga los datos del proyecto |
| **Reunir requerimientos:** | Registro de proyectos, sistema de notificación , base de datos y un sistema para validar que no haya errores|
| **Aspectos sobresalientes:** | ¿Qué pasa si hay algún error por parte del coordinador ?¿Si el sistema  encuentra en la edición de proyecto un proyecto parecido? |
| **Prioridad:** | Tiempo  (Alta)  | 
| **Riesgo:** | Tiempo - Costo (Media - Alta) |
