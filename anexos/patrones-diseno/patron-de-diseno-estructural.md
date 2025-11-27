# Anexo – Aplicación de Patrón de Diseño Estructural – Facade

## Patrones de Diseño Estructurales y su relación con SOLID

Los patrones de diseño estructurales se enfocan en cómo organizar, simplificar y conectar clases y objetos dentro de un sistema. Permiten reducir acoplamiento, encapsular relaciones complejas y facilitar la extensibilidad, trabajando en línea con principios SOLID como:

- **S (Responsabilidad Única):** cada clase cumple un rol bien definido.
- **O (Abierto/Cerrado):** permite extender funcionalidades sin modificar el código existente.
- **D (Inversión de Dependencias):** el cliente depende de una interfaz simplificada y no de subsistemas concretos.

---

# Propósito y Tipo del Patrón

## Propósito

En el sistema original, varios componentes del dominio (Proyecto, Etapa, Tarea, ResponsableDelProyecto) debían interactuar directamente con múltiples servicios técnicos como:

- ServicioProyecto
- ServicioEtapa
- ServicioNotificaciones

Este diseño generaba:

- Acoplamiento fuerte entre dominio y servicios técnicos
- Duplicación de lógica
- Dificultad para escalar o modificar servicios
- Complejidad excesiva para desarrolladores

El patrón **Facade** se utiliza para **simplificar el acceso** a estos servicios, encapsular la complejidad y proporcionar una única interfaz unificada.

## Tipo

Patrón estructural: **Facade**.

Adecuado porque:

- Simplifica el acceso al sistema.
- Reduce acoplamiento.
- Centraliza lógica repetitiva.
- Mejora la mantenibilidad.

---

# Motivación

Antes de implementar el patrón:

- Proyecto, Etapa y Tarea debían comunicarse directamente con distintos servicios.
- Se repetía lógica de validación, creación y notificaciones.
- Los servicios estaban expuestos al dominio generando acoplamiento.

**Clases del problema original:**

- Proyecto
- Etapa
- Tarea
- ResponsableDelProyecto
- ServicioProyecto
- ServicioEtapa
- ServicioNotificaciones

**Nueva clase introducida:**

- **GestorDeProyectosFacade**

Esta fachada:

- Reduce dependencia directa hacia los servicios
- Simplifica la API
- Centraliza validaciones y flujo de creación y persistencia

---

# Estructura de Clases

![diagrama](../../diagramas/01-diagrama-clases/01-patron-estructural-Fachada.png)

## Justificación Técnica de la Estructura de Clases

### **Proyecto**

- **Responsabilidad:** administrar reglas internas del proyecto.
- **Motivo:** interactúa con la fachada para evitar acoplamiento directo.
- **Colaboración:** delega creación y validaciones a la fachada.

---

### **Etapa**

- **Responsabilidad:** gestionar cambios de estado y responsables.
- **Motivo:** anteriormente llamaba directamente a servicios.
- **Colaboración:** usa la fachada para guardar y validar etapas.

---

### **Tarea**

- **Responsabilidad:** registrar tiempos y estados.
- **Motivo:** parte del flujo que interactúa con servicios externos.
- **Colaboración:** delega operaciones comunes en la fachada.

---

### **ResponsableDelProyecto**

- **Responsabilidad:** orquestar la gestión del proyecto.
- **Motivo:** interactúa con la fachada como punto central de operaciones.
- **Colaboración:** solicita acciones estandarizadas.

---

### **Servicios (ServicioProyecto / ServicioEtapa / ServicioNotificaciones)**

- **Responsabilidad:** lógica transversal interna.
- **Motivo:** son subsistemas a los que la fachada encapsula.
- **Colaboración:** la fachada orquesta su uso.

---

### **GestorDeProyectosFacade**

- **Responsabilidad:** exponer una API simplificada y unificada.
- **Motivo:** reducir acoplamiento y ocultar complejidad técnica.
- **Colaboración:** valida, crea, guarda y notifica en nombre del dominio.

---

## Explicación del Flujo Estructural

1. Una clase del dominio solicita una operación (crear proyecto, guardar etapa, enviar notificación).
2. En lugar de llamar directamente a los servicios técnicos, **llama a `GestorDeProyectosFacade`**.
3. La fachada:
   - Valida reglas
   - Orquesta servicios
   - Maneja errores
   - Envía notificaciones
4. El dominio se mantiene **limpio y con responsabilidad única**.
5. Se elimina acoplamiento y el sistema se vuelve **extensible y mantenible**.
