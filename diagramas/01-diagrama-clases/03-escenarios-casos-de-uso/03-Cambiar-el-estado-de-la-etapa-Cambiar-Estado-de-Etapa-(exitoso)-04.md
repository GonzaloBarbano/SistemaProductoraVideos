| **Nombre del escenario:**|Flujo principal -Cambiar Estado de Etapa (exitoso) | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | cambiar el estado de la etapa| | **ID Única:** | 4 |
| **Área** |Sistema de Gestión de Proyectos y Etapas | | | |
| **Actor(es):** |Responsable de la etapa, Servicio de notificaciones.  | | | |
| **Descripción:** |Modificar el estado de una etapa respetando reglas de negocio establecidas.| | | |

| **Activar Evento:** |El responsable de la etapa entra a la página para cambiar el estado de la etapa | **Identificadores e iniciadores de caso de uso** |
|---|---|---|
| **Tipo de señal:** | ☐ Externa | ☑️ Temporal | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El responsable de la etapa  abre el detalle de la etapa.| El sistema recibe la orden del responsable para mostrar el detalle de la etapa |                                                                                                                                        
| 2. El sistema muestra estado actual y opciones: Pendiente, En curso, Finalizada.| El sistema le muestra todas las opciones y el responsable se fija en las de el estado actual  |
| 3. El responsable de la etapa selecciona un nuevo estado y confirma. |El sistema recibe la información de las opción elegida.  |
| 4. El sistema valida reglas|El sistema revisa que la información comparándolo con las reglas establecidas |
| 5. El sistema actualiza el estado de la etapa. |El sistema termina de revisar la información y procede con el cambio |
| 6. El sistema registra el cambio en el historial. |El cambio es guardado en una base de datos |
| 7. El servicio de notificaciones envía notificación al coordinador | El sistema le envía una notificación al servicio para que le envíe una notificación al coordinador.Y mientra no reciba la notificación del que el proceso fue exitoso no pasa al siguiente paso |
| 8. El sistema muestra información al responsable de la etapa. |El sistema recibe la notificación exitosa por parte del servicio de notificaciones y se lo muestra al responsable |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Que esté designado el responsable de la etapa. |
| **Poscondiciones:** | La etapa cambia de estado |
| **Suposiciones:** | El responsable de la etapa tuvo avances en el proyecto|
| **Reunir requerimientos:** | Sistema de notificación, Sistema de gestión de etapas , base de datos  |
| **Aspectos sobresalientes:** | ¿Si el administrador quiere cambiar el estado de la etapa?¿Si en la validación encuentra un error ? |
| **Prioridad:** | Tiempo  (Bajo)  | 
| **Riesgo:** | Tiempo - Costo ( Bajo- Medio) |
