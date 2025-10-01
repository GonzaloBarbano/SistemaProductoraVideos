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

En el diagrama se observa cómo cada clase queda enfocada en una única responsabilidad:

- **Proyecto** se ocupa solo de la definición básica, mientras que EstadísticaProyecto maneja estadísticas y TiempoProyecto los cálculos temporales.

- **Etapa** concentra el flujo de trabajo, pero se apoya en CalendarioEtapa para gestionar tiempos y demoras.

- **Notificación** se limita al contenido del mensaje, delegando la programación a ProgramadorNotificaciones y los distintos medios de envío a CanalNotificacion.

De esta forma, cada clase tiene un único motivo de cambio, reflejando correctamente la aplicación del principio SOLID. Esto asegura mayor cohesión interna, reduce el acoplamiento y facilita la escalabilidad del sistema audiovisual de Vizion Estudio.
