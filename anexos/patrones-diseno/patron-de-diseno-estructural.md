# Anexo – Aplicación de Patrón de Diseño Estructural – Fachada (Facade)

## Patrones de Diseño Estructurales y su Relación con SOLID

Los patrones estructurales se enfocan en cómo se organizan y conectan clases y objetos para reducir acoplamiento, mejorar cohesión y permitir estructuras más flexibles y mantenibles.

Relación con SOLID:

* **S — Responsabilidad Única:** Separan responsabilidades distribuyendo funciones en clases específicas.
* **O — Abierto/Cerrado:** Permiten extender funcionalidades mediante envoltorios, adaptadores o fachadas sin modificar código existente.
* **L — Sustitución de Liskov:** El uso de interfaces y abstracciones permite intercambiar implementaciones sin alterar el comportamiento del sistema.
* **I — Segregación de Interfaces:** Favorecen interfaces pequeñas y específicas cuando el patrón lo requiere.
* **D — Inversión de Dependencias:** Promueven depender de abstracciones en lugar de implementaciones concretas.

---

## Propósito y Tipo del Patrón

### Propósito del Patrón Fachada

La **Fachada** provee una interfaz simple y unificada para acceder a funcionalidades complejas de múltiples subsistemas. Reduce la complejidad y oculta detalles internos del sistema.

### Tipo de patrón

**Patrón estructural**, utilizado para organizar y simplificar interacciones entre componentes.

### Problema que resuelve

En el sistema existía duplicación de código, múltiples dependencias entre clases y necesidad de coordinar varios servicios. Esto generaba acoplamiento fuerte, complejidad y poca mantenibilidad.

La fachada encapsula y orquesta estas operaciones, centralizando la lógica del caso de uso.

---

## Motivación

En este caso real del **Sistema de Gestión de Proyectos Audiovisuales**, el problema estructural surge por la forma en que las clases del dominio interactúan entre sí. Actualmente, componentes como `Proyecto`, `Etapa`, `Tarea`, `ResponsableDelProyecto` y los servicios (`ServicioProyecto`, `ServicioEtapa`, `ServicioNotificaciones`) están **fuertemente acoplados**. Cada capa conoce detalles internos de otras, lo que genera alta dependencia y dificulta la evolución del sistema.

Ejemplos del problema real observado:

* **`Proyecto` depende directamente de `ServicioProyecto`**, y `Etapa` depende de `ServicioEtapa`, creando vínculos rígidos entre la lógica del dominio y los servicios.
* `Etapa` genera notificaciones a través de `ServicioNotificaciones`, mezclando responsabilidades (violación de SRP).
* `ResponsableDelProyecto` cambia estados directamente en `Etapa`, provocando una dependencia circular en el comportamiento.
* Agregar nuevas reglas, flujos o servicios externos (p. ej., WhatsApp, auditorías) implica modificar múltiples clases del dominio.

El patrón estructural **Facade** ofrece una solución para **organizar dependencias, ocultar complejidad y reducir el acoplamiento entre capas**.

---

## Profundización del Problema en el Sistema

Al analizar el diseño del sistema se detectó que la lógica del dominio está fuertemente entrelazada con los servicios externos, generando los siguientes problemas:

### 1. Dependencias rígidas entre el dominio y los servicios

Las clases del dominio ejecutan directamente validaciones, persistencia y notificaciones, mezclando niveles de abstracción y violando **DIP** y **SRP**.

### 2. Dificultad para extender el sistema

Cualquier cambio requiere modificar varias clases, rompiendo **OCP**.  
Ejemplos:

* nuevos repositorios,
* nuevos canales de notificación,
* nuevas reglas de validación.

### 3. Alto acoplamiento entre etapas, tareas y servicios

Las clases conocen demasiados detalles sobre cómo se guardan, validan o notifican datos, dificultando:

* pruebas unitarias,
* mantenimiento,
* incorporación de cambios futuros.

---

## Cómo el Patrón Estructural Soluciona el Problema

El patrón **Facade** introduce una única clase que actúa como **punto de acceso** para las operaciones del sistema. Esta fachada:

* encapsula la complejidad de los servicios,
* organiza los flujos de trabajo,
* y evita que las clases del dominio dependan de múltiples servicios externos.

### Beneficios obtenidos

* Menor acoplamiento entre capas.
* Mayor encapsulamiento de la lógica de orquestación.
* Mayor extensibilidad sin modificar clases del dominio.
* Mayor claridad arquitectónica.

---

## Clases Implicadas en el Problema

Las clases afectadas por el acoplamiento excesivo son:

* `Proyecto`
* `Etapa`
* `Tarea`
* `ResponsableDelProyecto`
* `ServicioProyecto`
* `ServicioEtapa`
* `ServicioNotificaciones`
* `RepositorioProyecto`
* `RepositorioEtapas`

Estas clases mezclaban responsabilidades del negocio con lógica de infraestructura.

---

## Nueva Clase Incorporada con el Patrón Facade

Se incorpora **una única clase adicional**:

### **GestorDeProyectosFacade**

Responsabilidades:

* Centralizar operaciones como creación de proyectos, gestión de etapas y envío de notificaciones.
* Utilizar internamente los servicios (`ServicioProyecto`, `ServicioEtapa`, `ServicioNotificaciones`).
* Eliminar dependencias directas entre el dominio y los servicios.
* Reducir acoplamiento y mejorar orden arquitectónico.

---

## ✔ Justificación Técnica de la Solución Propuesta

La aplicación del patrón **Facade** se justifica porque:

1. **Reduce el acoplamiento** al evitar que el dominio dependa de múltiples servicios externos.
2. **Mejora la cohesión**, concentrando en un único lugar la lógica de coordinación.
3. **Cumple DIP**, ya que el dominio pasa a depender de una fachada estable en lugar de implementaciones concretas.
4. **Facilita la extensibilidad (OCP)**: nuevos servicios o reglas pueden incorporarse dentro de la fachada sin afectar al dominio.
5. **Ordena la arquitectura**, separando:
   * dominio (reglas del negocio),
   * servicios (infraestructura),
   * fachada (orquestación).
6. **Mejora pruebas y mantenimiento**, permitiendo testear el dominio sin involucrar servicios externos.

En conjunto, el patrón aporta **simplicidad, escalabilidad y claridad arquitectónica**.

---

# 📌 Diagrama de Clases – Aplicación del Patrón Facade

> ![diagrama](../../diagramas/01-diagrama-clases/01-patron-estructural-Fachada.png)



