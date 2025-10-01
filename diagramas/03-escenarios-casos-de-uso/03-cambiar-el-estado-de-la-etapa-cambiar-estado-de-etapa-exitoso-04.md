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
| 1. El responsable de la etapa  abre el detalle de la etapa.| Pantalla de detalle de la etapa. |                                                                                                                                        
| 2. El sistema muestra estado actual y opciones: Pendiente, En curso, Finalizada.| Sección de estado con opciones disponibles: Pendiente, En curso, Finalizada.  |
| 3. El responsable de la etapa selecciona un nuevo estado y confirma. |Nuevo estado seleccionado en el formulario de la etapa.   |
| 4. El sistema valida reglas|Reglas de validación: avance autorizado por coordinador, cambios permitidos entre estados. |
| 5. El sistema actualiza el estado de la etapa. |Estado actualizado en el registro de la etapa.  |
| 6. El sistema registra el cambio en el historial. |Registro de historial con información de cambio: etapa, estado anterior, estado nuevo, fecha y hora. |
| 7. El servicio de notificaciones envía notificación al coordinador | Notificación de cambio de estado enviada al coordinador. |
| 8. El sistema muestra información al responsable de la etapa. |Mensaje de confirmación en pantalla. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Que esté designado el responsable de la etapa. |
| **Poscondiciones:** | La etapa cambia de estado |
| **Suposiciones:** | El responsable de la etapa tuvo avances en el proyecto|
| **Reunir requerimientos:** | Sistema de notificación, Sistema de gestión de etapas , base de datos  |
| **Aspectos sobresalientes:** | ¿Si el administrador quiere cambiar el estado de la etapa?¿Si en la validación encuentra un error ? |
| **Prioridad:** | Tiempo  (Bajo)  | 
| **Riesgo:** | Tiempo - Costo ( Bajo- Medio) |
