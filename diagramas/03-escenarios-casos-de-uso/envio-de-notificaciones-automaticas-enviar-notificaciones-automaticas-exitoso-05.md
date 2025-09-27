| **Nombre del escenario:**|Flujo principal -Enviar Notificaciones Automáticas (exitoso) | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** |Envío de notificaciones automáticas  | | **ID Única:** | 5 |
| **Área** |Sistema de Gestión de notificaciones | | | |
| **Actor(es):** | Coordinador/Responsable de etapa, Servicio de notificaciones, destinatario| | | |
| **Descripción:** |  Avisar automáticamente a los usuarios responsables ante eventos relevantes en proyectos o etapas| | | |

| **Activar Evento:** | El sistema registra algo que tiene que notificar  | **Identificadores e iniciadores de caso de uso** |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El Responsable realiza una acción relevante (ej: cambiar estado).|Evento generado:Cambio de estado de la etapa: Pendiente , En curso , Finalizada  |  
| 2. El sistema identifica destinatarios según el evento. | Busca dentro de la base de datos  |
| 3. El sistema determina el canal de notificación según preferencias de cada usuario.|El sistema termina de buscar la información  de la base de datos |
| 4. El sistema compone mensajes con datos del proyecto/etapa. |Hace un mensaje con la información  |
| 5. El servicio de notificaciones envía la notificación al destinatario |El sistema manda el mensaje/notificación |
| 6. El servicio de notificaciones devuelve resultado (éxito) | El sistema se auto notifica que el mensaje fue enviado con éxito  |
| 7. El servicio de notificaciones envía el resultado a otros sistemas|El sistema hace un mensaje con la información.| 
| 8. El sistema registra el envío en el historial de notificaciones. | El sistema lo guarda dentro base de datos |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Que el proyecto tenga un avance |
| **Poscondiciones:** | Que el destinatario tenga la información |
| **Suposiciones:** | Que el proyecto o etapa tenga avances para notificar |
| **Reunir requerimientos:** | Sistema de notificación |
| **Aspectos sobresalientes:** | ¿Qué pasa si la notificación no llega al destinatario?¿Que pasaria si el destinatario tiene varios canales de notificación (se envia a todos o solo a uno) ?|
| **Prioridad:** | Tiempo (bajo) |                 
| **Riesgo:** | Tiempo - Costo (Bajo) |
