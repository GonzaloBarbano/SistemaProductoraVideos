# Sesión JAD – Sistema de Gestión de Proyectos Audiovisuales

**Fecha:** 14/03/2025 – 11:00hs
**Lugar:** Google Meet
**Participantes:**
- Laura González (Productora general – Vizion Estudio)
- Martín Suárez (Responsable de Edición – Vizion Estudio)
- Carla Paredes (Asistente de producción – Vizion Estudio)
- Marcos Díaz (Analista funcional – SolucionesDev)
- Julieta Romero (UX/UI – SolucionesDev)

---

## 1 Objetivo de la sesión
Definir responsabilidades, reglas funcionales y restricciones del sistema orientado a objetos, para validar el modelo de clases y el flujo de trabajo representado en los diagramas actuales (CU01 – Crear/Editar Proyecto, CU02 – Gestionar Etapas).
Responsabilidades identificados son:

Productor/Admin:tiene la responsabilidad de crear o modificar etapas.

Responsable de Etapa: Tiene las responsabilidades de asignar Fechas Límite de la etapa , Gestión de Alertas (Por los avisos por retrasos) , Organizar el Trabajo.

Asistente: Tiene la responsabilidad del Registro de Observaciones (Registra las observaciones).

Reglas de Negocio:
1_Configuración de Etapas: El flujo de etapas debe ser configurable, ya que no todos los proyectos siguen el mismo flujo. Solo el Productor/Admin tiene permisos para crear o modificar etapas.

2_Colaboración: Debe haber un "responsable principal" por etapa, pero el sistema debe permitir subtareas colaborativas o ayudantes.

3_Registro Histórico: Se debe mantener un historial de incidencias y observaciones internas (comentarios de seguimiento) en cada etapa.

4_ Registro de Tiempos: El sistema debe registrar automáticamente el tiempo estimado versus el tiempo real por etapa y proyecto para generar estadísticas de retraso.

5_ Visualización: La vista principal debe mostrar todos los proyectos activos con filtros por estado, responsable y tipo de proyecto.


Validaciones y Restricciones

1. Fechas Límite: Se deben manejar fechas límite obligatorias por etapa.
2. Alertas: Se deben enviar alertas de retraso 24 horas antes de la fecha límite.
3. Notificaciones: El sistema debe enviar notificaciones automáticas por correo electrónico y WhatsApp cuando una etapa se completa.
4. Material: En la versión inicial, la subida de material se limitará a links externos (Drive o Vimeo), aunque el campo debe quedar preparado para futuros archivos.
---

## 2 Matriz de Registro JAD
Minimo 10 registros completos extraidos de la Sesión JAD.

La Matriz de Registro JAD completada con un mínimo de 10 registros extraídos de las fuentes es la siguiente, incluyendo el registro de ejemplo proporcionado:

| **Pregunta Clave (según guía JAD)** | **Respuesta / Decisión del Usuario** | **Clases Candidatas** | **Atributos / Métodos / Responsabilidades Detectadas** | **Observaciones** |
|------------------------------------|--------------------------------------|------------------------|--------------------------------------------------------|------------------|
| ¿Quién puede crear o modificar las etapas de un proyecto? | Solo el Productor/Admin. | `Proyecto`, `Etapa`, `Usuario`. | `Etapa.crear()`, `Etapa.modificar()`, `Usuario.rol`. | Confirmar permisos en el modelo actual. |
| ¿Puede una etapa tener más de un responsable? | Debe haber un **responsable principal**, pero el sistema debe permitir subtareas colaborativas (ayudantes). | `Etapa`, `Usuario`, `Tarea`. | `Etapa.responsable`, `asignarResponsable()`. | Mantener un responsable principal en el modelo de `Etapa`. |
| ¿El sistema debe permitir agregar seguimiento u observaciones internas? | Sí, para agregar comentarios de seguimiento y un historial de incidencias. | `Etapa`, `Observación`. | `Etapa.observaciones\[]`, `registrarObservación()`, `Observación.tipo` (incidencia, comentario), `Observación.usuario`, `Observación.fecha`. | El registro de incidencias debe incluir fecha, usuario y tipo. |
| ¿Se deben poder guardar enlaces o archivos externos? | Se necesitan guardar enlaces (Drive, Vimeo) dentro del sistema. Se limita a links externos en esta versión, pero se deja preparado el campo. | `Etapa`, `Archivo/Link`. | `Etapa.links\[]`. | La subida de archivos se pospone, priorizando enlaces externos en V1. |
| ¿Cómo se notifica al siguiente responsable que una etapa ha finalizado? | El sistema debe enviar **notificaciones automáticas** por mail y WhatsApp al completarse la etapa. | `Notificación`, `Usuario`. | `generarAlerta()`, `Notificación.destinatario`, `Notificación.tipo`. | Las notificaciones son críticas para asegurar que el siguiente responsable inicie su trabajo sin consultar. |
| ¿Qué otros eventos importantes deben generar notificaciones? | Se debe notificar al productor general cuando un proyecto cambia a un **estado importante** (ej. "en revisión" o "finalizado"). | `Proyecto`, `Notificación`, `Usuario`. | `Proyecto.cambiarEstado()`, `Usuario.rol` (Productor/Admin). | El productor requiere seguimiento de los hitos clave. |
| ¿Se requieren fechas límite obligatorias para las etapas? | Sí, son obligatorias para evitar retrasos. | `Etapa`. | `Etapa.fecha límite` (obligatorio). | La fecha límite debe ser ingresada por el productor o el responsable de la etapa al crearla. |
| ¿Con qué anticipación se desean las alertas de retraso? | 24 horas antes de la fecha límite. | `Etapa`, `Notificación`. | `generarAlerta()`. | El margen de 24 horas fue aceptado por todos los participantes. |
| ¿Las tareas deben manejar prioridades? | Sí, las tareas deben tener prioridades (alta / media / baja) para mejor organización. | `Tarea`, `Etapa`. | `Etapa.prioridad`. | Se propone mostrar la prioridad con colores (rojo, amarillo, verde) en el tablero. |
| ¿El sistema debe registrar el tiempo de ejecución? | Sí. Debe registrar automáticamente el **tiempo estimado vs. real** por etapa y proyecto. | `Proyecto`, `Etapa`. | `calcularDuraciónReal()`. | Esto es necesario para generar estadísticas de retraso al cierre. |

---

Hemos detectado requerimientos clave para el MVP, como las notificaciones automáticas y el manejo de incidencias. ¿Le gustaría que profundicemos en las características identificadas para la **versión 2 (v2)**, como la aprobación de etapas por parte del cliente y las estadísticas de facturación?
---

## 3 Issues e inconsistencias detectadas

| **ID** | **Descripción del Issue / Inconsistencia** | **Impacto** | **Estado** | **Link a Issue (GitHub)** |
|--------|---------------------------------------------|--------------|-------------|-----------------------------------|
| #66 | En el caso de uso UC1 (Crear/Editar Proyecto) no se menciona explícitamente la relación con el Responsable de Etapa, aunque en las reglas de negocio se indica que este actor gestiona fechas y alertas por etapa. | medio | Pendiente | [🔗 Issue #66 – Inconsitencia 1 dectectada en JAD](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/66) |
| #67 | En UC2 (Gestionar Etapas) el caso de uso “Alertar Posible Retraso” depende del sistema de notificaciones, pero no se especifica en el diagrama si la alerta se genera automáticamente o si la dispara el usuario. | alto | Pendiente | [🔗 Issue #67 – Inconsitencia 2 dectectada en JAD](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/67) |
| #68 | En las Reglas de Negocio, se menciona “Registro de tiempos estimado vs real” y “Estadísticas de retraso”, pero no hay ningún caso de uso o elemento que represente ese cálculo. | alto | Pendiente | [🔗 Issue #68 – Inconsitencia 3 dectectada en JAD](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/68) |
| #69 | Las restricciones de envío de alertas por correo o WhatsApp aparecen en las validaciones, pero en UC5 y UC2 sólo se modela un “Servicio de Notificaciones” genérico sin distinguir canales. | Medio | Pendiente | [🔗 Issue #69 – Inconsitencia 4 dectectada en JAD](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/69) |
| #70 | En UC2, el actor Asistente de Producción puede registrar observaciones, pero no está claro si tiene permiso para modificarlas o solo crearlas. | Bajo | Pendiente | [🔗 Issue #70 – Inconsitencia 5 dectectada en JAD](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/70) |
| #71 | En UC1 y UC2 se incluyen notificaciones automáticas (UC5), pero no existe una precondición que garantice que el Servicio de Notificaciones esté disponible. | Medio | Pendiente | [🔗 Issue #71 – Inconsitencia 6 dectectada en JAD](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/71) |