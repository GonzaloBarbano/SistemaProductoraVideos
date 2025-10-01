# Principio de Sustitución de Liskov (LSP)

---

##  Propósito y Tipo del Principio SOLID
El **Principio de Sustitución de Liskov (LSP)** establece que los objetos de una subclase deben poder sustituir a los de su superclase **sin alterar el comportamiento esperado** del sistema.  
Forma parte de los principios de **diseño orientado a objetos** dentro de **SOLID** y su propósito principal es **garantizar jerarquías de herencia consistentes y predecibles**.

---

##  Motivación
Un problema frecuente ocurre cuando una subclase **rompe el contrato** definido en la superclase, generando resultados inesperados.  

**Ejemplo del mundo real:**  
Imaginemos una jerarquía de **figuras geométricas**:  
- La clase base `Figura` define el método `area()`.  
- `Rectangulo` y `Circulo` son subclases que implementan `area()` de acuerdo a sus atributos (`ancho/alto` o `radio`).  

Gracias al LSP, cualquier instancia de `Rectangulo` o `Circulo` puede sustituir a `Figura` en el sistema sin que cambie el comportamiento esperado.  

Si una subclase violara este contrato (ejemplo: redefinir `area()` de forma incompatible), rompería la lógica de toda la jerarquía.

---

##  Explicación de Herencia
En programación orientada a objetos, la herencia establece una relación **“es-un”**:  
- `Rectangulo` **es una** `Figura`.  
- `Circulo` **es una** `Figura`.  

Para cumplir con LSP, las subclases (`Rectangulo`, `Circulo`) deben implementar `area()` de forma **coherente** con la definición abstracta en `Figura`.  
Esto asegura que puedan sustituir a la superclase en cualquier contexto donde se espere una `Figura`.

---
##  Estructura de Clases

El siguiente diagrama UML muestra la utilización solid LSP:
![LSP](../../diagramas/01-diagrama-clases/01-solid-03-lsp.png)
--- 
## ⚙️ Justificación Técnica
En el diagrama UML:  
- La clase abstracta `Figura` define el contrato `area()`.  
- `Rectangulo` implementa `area()` usando ancho y alto.  
- `Circulo` implementa `area()` usando el radio.  

Cualquier instancia de `Rectangulo` o `Circulo` puede sustituir a `Figura`, ya que ambas respetan el contrato definido.  