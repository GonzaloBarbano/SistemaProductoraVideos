| **Nombre del escenario:**|Flujo principal -Asignar Responsable a Etapa (exitoso) | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Asignar Responsable| | **ID Única:** | 3 |
| **Área** | Área  de seguimiento del proyecto y etapa , Área de asignación de trabajo| | | |
| **Actor(es):** | Coordinador, usuario responsable, servicio de notificaciones.  | | | |
| **Descripción:** | Asignar el responsable de una etapa y notificarlo.| | | |

| **Activar Evento:** | El coordinador entra en los detalles del proyecto para asignar un responsable del proyecto| **Identificadores e iniciadores de caso de uso** |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1.El coordinador abre el detalle del proyecto y selecciona una etapa. |Lista de etapas del proyecto. |                                                                                                                                        
| 2. El sistema muestra los datos actuales de la etapa. |Datos actuales de la etapa seleccionada (responsable, fechas, estado, observaciones).|
| 3. El coordinador selecciona en Asignar responsable. |Opción “Asignar responsable”.|
| 4. El sistema despliega un selector de usuarios.|Selector de usuarios con información: nombre, apellido, proyectos finalizados, jerarquía en la empresa.  |
| 5. El coordinador elige al responsable y confirma. | Usuario seleccionado en el selector.|
| 6. El sistema valida el usuario y actualiza la etapa. |Reglas de validación de usuario + actualización de responsable en la etapa.|
| 7. El sistema registra el cambio en el historial (quién, a quién, cuándo). | Registro de historial: responsable asignado, responsable anterior, fecha y hora.|
| 8. El servicio de notificaciones envía un aviso al usuario responsable indicando la  asignación. |Notificación de asignación enviada al nuevo responsable.|
| 9. El sistema muestra confirmación al coordinador. |Mensaje de confirmación en pantalla.|

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Que el proyecto exista y tenga las etapas definidas  |
| **Poscondiciones:** |El usuario responsable es designado  |
| **Suposiciones:** | El coordinador tiene usuarios libres para aceptar las etapas del proyecto|
| **Reunir requerimientos:** | sistema de notificación , aplicaciòn para asignar las etapas, Registro de proyectos y una base de datos |
| **Aspectos sobresalientes:** | ¿Que pasa si el coordinador elige un usuario que no está disponible?¿Si no llega la notificación al usuario? |
| **Prioridad:** | Tiempo  (Alta)  | 
| **Riesgo:** | Tiempo - Costo ( Alta) |
