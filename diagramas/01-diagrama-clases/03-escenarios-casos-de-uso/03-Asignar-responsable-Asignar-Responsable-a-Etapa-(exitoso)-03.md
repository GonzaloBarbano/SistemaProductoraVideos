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
| 1.El coordinador abre el detalle del proyecto y selecciona una etapa. |El sistema muestra la lista de etapas.Y el coordinador selecciona una etapa|                                                                                                                                        
| 2. El sistema muestra los datos actuales de la etapa. |El sistema entra en la base de datos y busca los datos de la etapa solicitada|
| 3. El coordinador selecciona en Asignar responsable. |El sistema lee la acción y prepara el selector de usuarios|
| 4. El sistema despliega un selector de usuarios.|El sistema espera la respuesta del coordinador |
| 5. El coordinador elige al responsable y confirma. |El coordinador elige y el sistema recibe la información y empieza a procesar la|
| 6. El sistema valida el usuario y actualiza la etapa. |El sistema termina de procesar la información y verifica la información y lo muestra en la pagina|
| 7. El sistema registra el cambio en el historial (quién, a quién, cuándo). |El usuario ve el cambio y el sistema guarda el cambio en la base de datos|
| 8. El servicio de notificaciones envía un aviso al usuario responsable indicando la  asignación. |El sistema le manda la información al servicio de notificación que le tiene que enviar una notificación al usuario responsable.Y el sistema aguarda la confirmación de que llego la notificación al usuario.|
| 9. El sistema muestra confirmación al coordinador. |El sistema al llegar la notificación se lo muestra al coordinador.Y la notificación se guarda en una base de datos.|

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Que el proyecto exista y tenga las etapas definidas  |
| **Poscondiciones:** |El usuario responsable es designado  |
| **Suposiciones:** | El coordinador tiene usuarios libres para aceptar las etapas del proyecto|
| **Reunir requerimientos:** | sistema de notificación , aplicaciòn para asignar las etapas, Registro de proyectos y una base de datos |
| **Aspectos sobresalientes:** | ¿Que pasa si el coordinador elige un usuario que no está disponible?¿Si no llega la notificación al usuario? |
| **Prioridad:** | Tiempo  (Alta)  | 
| **Riesgo:** | Tiempo - Costo ( Alta) |
