# Principio de Responsabilidad Única (SRP)

## Propósito y Tipo del Principio SOLID

El Principio de Responsabilidad Única (SRP) establece que una clase debe tener una única razón para cambiar.  
En el sistema de gestión de proyectos audiovisuales de Vizion Estudio se identificaron clases que concentraban múltiples responsabilidades, lo cual genera mayor acoplamiento y dificulta el mantenimiento.  
Aplicar SRP permite separar las responsabilidades, logrando clases más cohesivas, fáciles de probar y extender.

---

## Motivación

Durante el diseño inicial, algunas clases mezclaban diferentes responsabilidades:

- **Proyecto**: registraba datos básicos, tipos de proyecto para estadísticas y además calculaba tiempos totales.
- **Etapa**: definía pasos, gestionaba estados y también controlaba fechas de inicio y fin.
- **Notificación**: enviaba mensajes, programaba envíos y además gestionaba canales de comunicación.

Estos múltiples motivos de cambio en una misma clase generaban riesgo de que una modificación en reglas de negocio afectara áreas no relacionadas.  
Con SRP se propone dividir cada una en clases más específicas:

- **Proyecto** (solo datos básicos), **EstadísticaProyecto** (estadísticas), **TiempoProyecto** (cálculo de tiempos).
- **Etapa** (unidad de trabajo) y **CalendarioEtapa** (gestión de fechas).
- **Notificación** (mensaje y destinatario), **ProgramadorNotificaciones** (programación de envío) y **CanalNotificacion** (mail, WhatsApp, etc.).

---

## Estructura de Clases

El siguiente diagrama UML muestra la refactorización propuesta al aplicar SRP:
![SRP](../../diagramas/01-diagrama-clases/%2001-solid-01-srp.png)

---

## Justificación Técnica

Cada clase presenta una única razón de cambio, cumpliendo con el principio SRP.

- **Proyecto** podría modificarse únicamente si se alteran los datos generales que gestiona (por ejemplo, agregar un nuevo atributo como “cliente asociado”).
- **TiempoProyecto** cambiaría solo si se modifican las reglas de cálculo de duración o la forma de registrar las fechas de inicio y fin.
- **EstadisticaProyecto** se vería afectada únicamente si se redefinen las métricas o indicadores utilizados para evaluar el rendimiento del proyecto.
- **NotificacionProyecto** cambiaría únicamente si se agregan o eliminan canales de comunicación, o si se ajustan las condiciones que disparan una notificación.

Esta separación permite que el sistema evolucione sin afectar otras partes, facilita las pruebas unitarias y promueve un diseño coherente con los principios de alta cohesión y bajo acoplamiento.
