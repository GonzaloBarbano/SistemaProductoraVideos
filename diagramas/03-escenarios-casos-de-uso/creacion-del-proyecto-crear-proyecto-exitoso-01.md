| **Nombre del escenario:**|Flujo principal-Crear Proyecto exitoso | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | creación del Proyecto   | | **ID Única:** | 1 |
| **Área** |Sistema de Gestión de Proyectos| | | |
| **Actor(es):** | Productor/Coordinador, Cliente/Administrador | | | |
| **Descripción:** |  Registrar o actualizar un proyecto con sus datos mínimos y dejarlo disponible para seguimiento.| | | |

| **Activar Evento:** | El cliente ingresa en la página | **Identificadores e iniciadores de caso de uso** |
|---|---|---|
| **Tipo de señal:** | ☑️Externa | ☐ Temporal | |
 
| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El actor navega a Proyectos y selecciona Nuevo. |El acto selecciona nuevo o editar  y el sistema le permite acceder al formulario | 
| 2.El sistema muestra un formulario con campos: nombre, cliente, fechas de inicio y fin estimada, estado, observaciones. | Formulario de etapa con campos: nombre,cliente,fecha de inicio y fin estimada,estado,observaciones.  |
| 3.  El actor completa los campos obligatorios. | El actor debe tener en claro los campos obligatoria a rellenar |
| 4.  El sistema valida (obligatorios, formato de fechas, duplicados de nombre).  | El sistema empieza a revisar si hay algún error |
| 5.  Si hay errores, el sistema resalta los campos inválidos y muestra mensajes. | El sistema termina con la revisión |
| 6. El sistema persiste el proyecto y registra auditoría (quién/cuándo).|El sistema registra el proyecto automaticamente  |
| 7. El Servicio de Notificaciones envía aviso de "proyecto creado/editado" al cliente y/o administrador.|Mensaje de confirmación mandado por el sistema  |
| 8. El sistema confirma y redirige al detalle del proyecto.|El sistema después de confirmar que le llego el mensaje a cliente y al administrador  |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Usuario autenticado con permiso; el nombre del proyecto no debe estar duplicado. |
| **Poscondiciones:** | Proyecto persistido y disponible en listados/tablero. |
| **Suposiciones:** | Que conozca la productora y conozca los detalles proyecto   |
| **Reunir requerimientos:** | Que tenga una computadora , un sistema para validar que no haya errores , un sistema para las notificaciones y una base de datos |
| **Aspectos sobresalientes:** | ¿Qué pasa si hay un error en los datos ? ¿Qué pasa si no hay disponibilidad para aceptar el trabajo?|
| **Prioridad:** | Tiempo  (Media)  | 
| **Riesgo:** | Tiempo - Costo (Bajo) |

 