# Anexo – Aplicación de Patrón de Diseño de Comportamiento – Observer

## Patrones de Diseño de Comportamiento y su relación con SOLID

Los patrones de diseño de comportamiento definen cómo los objetos interactúan entre sí para distribuir responsabilidades y evitar dependencias rígidas. Su objetivo es favorecer la extensibilidad, reducir el acoplamiento y permitir que nuevas variantes de comportamiento se incorporen sin modificar el código existente.

### Relación con SOLID

- **S – Responsabilidad Única:** cada clase cumple un único rol (Sujeto u Observador).
- **O – Abierto/Cerrado:** se pueden agregar nuevos observadores sin modificar las clases que generan los eventos.
- **L – Sustitución de Liskov:** cualquier clase que implemente `Observer` puede reemplazarse sin afectar el sistema.
- **I – Segregación de Interfaces:** cada rol implementa sólo los métodos necesarios (Observer / Subject).
- **D – Inversión de Dependencias:** los sujetos dependen de la abstracción `Observer`, no de observadores concretos.

---

## Propósito y Tipo del Patrón

### Propósito

Resolver el problema de notificación múltiple cuando cambia el estado de una **Etapa** o una **Tarea**, evitando acoplamiento directo entre el dominio y los servicios externos (notificaciones, auditoría, responsable del proyecto, etc.).  
El sistema original contenía lógica repetida en varias clases y mezclaba reglas de negocio con infraestructura, dificultando la extensión del comportamiento.

### Tipo

**Patrón de Comportamiento – Observer.**  
Framework que permite que múltiples objetos se suscriban para recibir actualizaciones automáticas cuando ocurre un cambio relevante en otro objeto.

---

## Motivación

En el Sistema de Gestión de Proyectos Audiovisuales, cada vez que una **Etapa** o **Tarea** cambiaba de estado, varios componentes necesitaban enterarse:

- Responsable del proyecto
- Servicio de Notificaciones (Mail/WhatsApp)
- Servicio de Auditoría
- Panel del administrador
- Visores del cliente

### Problemas detectados en el diseño original

- Cada clase del dominio llamaba directamente a servicios externos (mal acoplamiento).
- El código de notificación estaba duplicado en varios puntos.
- Era difícil agregar nuevos interesados sin modificar múltiples clases.
- Mezcla entre reglas del dominio y funciones técnicas → violación de SRP.
- Dependencia directa del dominio hacia servicios concretos → violación de DIP.

### Cómo lo resuelve Observer

Mediante Observer:

1. **Etapa** y **Tarea** actúan como _Subjects_.
2. Mantienen una lista de objetos que desean ser notificados.
3. Cuando ocurre un cambio, generan un objeto **Evento** con la información del cambio.
4. Ejecutan `notificarObservers(evento)` sin conocer a los observadores concretos.
5. Observadores como **ServicioNotificaciones**, **ResponsableDelProyecto** y **ServicioAuditoria** reaccionan según su función.

### Importante

El método `notificarObservers()` **debe recibir un objeto `Evento`**, ya que:

- Los observadores necesitan saber **qué ocurrió**.
- El evento contiene datos clave:
  - tipo de cambio (estado, responsable, actualización),
  - ID de la etapa/tarea,
  - ID del proyecto,
  - nuevo estado o responsable asignado,
  - fecha y usuario que realizó la acción.

Sin este objeto, los observadores no tendrían información suficiente para actuar correctamente (enviar mensaje, registrar auditoría, actualizar panel, etc.).

---

## Estructura de Clases

![diagrama](../../diagramas/01-diagrama-clases/01-patron-comportamiento-Observer.png)

---

## Justificación Técnica de la Estructura de Clases

A continuación, se detalla el rol técnico de cada clase involucrada:

### **Subject (Etapa / Tarea)**

#### Etapa

- **Responsabilidad:** gestionar cambios de estado de una etapa dentro del proyecto.
- **Comportamiento que encapsula:** detección de eventos internos relevantes (cambio de estado, asignación de responsable).
- **Interacción:**
  - Registra observadores.
  - Genera un objeto `Evento`.
  - Llama a `notificarObservers(evento)`.
- **Justificación:** es indispensable como fuente de cambios que desencadenan notificaciones.

#### Tarea

- Misma lógica que Etapa, pero enfocada en tareas individuales del proyecto.
- Cualquier cambio (tiempos, estado, avance) debe ser notificado.

---

### **Observer (Interfaz)**

- **Responsabilidad:** definir el contrato para clases interesadas en recibir actualizaciones.
- **Justificación:** permite agregar observadores sin modificar Subjects (OCP).

---

### **Evento**

- **Responsabilidad:** transportar la información del cambio ocurrido.
- **Datos típicos:**
  - tipo de evento
  - id de la etapa/tarea
  - id del proyecto
  - estado anterior y nuevo
  - timestamp
- **Justificación:** indispensable (según observación del revisor) para que Observer funcione en un sistema real.

---

### Observadores Concretos

#### ServicioNotificaciones

- **Responsabilidad:** enviar emails o mensajes al equipo.
- **Interactúa:** recibe `Evento`, construye mensaje y envía notificación.
- **Justificación:** desacopla completamente la lógica de mensajería del dominio.

#### ResponsableDelProyecto

- **Responsabilidad:** recibir avisos automáticos de cambios relevantes del proyecto.
- **Justificación:** elimina la dependencia directa entre Etapa/Tarea y el responsable.

#### ServicioAuditoria

- **Responsabilidad:** registrar toda acción para trazabilidad.
- **Justificación:** recibe la información del evento sin alterar el dominio.

---

## Flujo del Comportamiento (cómo funciona)

1. **Un usuario cambia el estado de una Etapa o Tarea.**
2. La clase genera un **Evento** describiendo el cambio.
3. Se ejecuta `notificarObservers(evento)`.
4. Cada observador recibe el evento mediante `actualizar(evento)`.
5. Cada uno realiza su acción:
   - Notificaciones envía mails/mensajes.
   - Auditoría registra.
   - Responsable del Proyecto actualiza su panel.
6. El dominio permanece desacoplado y sin lógica de infraestructura.

Este flujo permite agregar nuevos observadores (por ejemplo, “ServicioAnalytics”) sin modificar ni una línea de código en **Etapa** ni **Tarea**, cumpliendo estrictamente con OCP y DIP.
