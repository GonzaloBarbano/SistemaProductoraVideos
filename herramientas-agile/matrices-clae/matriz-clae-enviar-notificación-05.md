# Matriz CLAE (CRUD) – [enviar-notificación]

**Proyecto:** Sistema de Gestión de Proyectos Audiovisuales  
**Caso de Uso:** [CUx - enviar-notificación]  

---

## 1 Tabla CLAE

> **Estructura:**  
> - **Filas:** Actividades internas del caso de uso (acciones o pasos del flujo).  
> - **Columnas:** Clases del sistema involucradas.  
> - **Celdas:** Letras **C**, **L**, **A**, **E** según la operación que se realiza sobre la clase.  
> - Si no aplica, dejar la celda vacía.  

|Actividad / Clase                  | Responsable de Etapa | Coordinador / Productor | Servicio de Notificaciones  |
|-----------------------------------|:--------------------:|:-----------------------:|:---------------------------:|
| Identificar destinatarios         |         L            |          L              |              C              |
| Determinar canal de envío         |                      |                         |              C              |
| Componer mensaje                  |                      |                         |              C              |
| Registrar envío en historial      |                      |                         |              C              |

> **Leyenda:**  
> **C**: Crear – **L**: Leer/Listar – **A**: Actualizar – **E**: Eliminar  

---

## 2 Métodos identificados

> Los métodos se derivan directamente de las operaciones (C/L/A/E) marcadas en la tabla.  
> Cada método deberá existir en la clase correspondiente del **diagrama de clases**, y reflejarse en su **Tarjeta CRC** y en el **diagrama de secuencia** del caso de uso.


| Clase                       | Método                                                   | Tipo | Parámetros                                 | Retorno | Actividad asociada |
|-----------------------------|-----------------------------------------------------------|------|--------------------------------------------|---------|---------------------|
| Responsable de Etapa        | `generarEventoNotificable(etapa: Etapa, cambio: Cambio)` | C    | etapa: Etapa, cambio: Cambio               | bool    | Disparar evento |
| GestorNotificaciones        | `identificarDestinatarios(evento: Evento)`               | L    | evento: Evento                              | List<Usuario> | Identificar destinatarios |
| GestorNotificaciones        | `determinarCanal(usuario: Usuario)`                     | L    | usuario: Usuario                            | Canal   | Determinar canal |
| GestorNotificaciones        | `componerMensaje(usuario: Usuario, datos: DatosNotif)`  | C    | usuario: Usuario, datos: DatosNotif         | Mensaje | Crear mensaje |
| Servicio Notificaciones     | `enviarNotificacion(destinatario: Usuario, mensaje: Mensaje)` | C | destinatario: Usuario, mensaje: Mensaje | bool | Enviar |
| Servicio Notificaciones     | `registrarEnvio(etapa: Etapa, canal: Canal, estado: Estado)` | C | etapa: Etapa, canal: Canal, estado: Estado | bool | Registrar historial |
| Sistema Integración         | `registrarResultadoExterno(envio: Envio, estado: Estado)` | C    | envio: Envio, estado: Estado               | bool    | Registrar respuesta |
| Notificacion (INotificacion) | `programarNotificacion(fecha: DateTime, mensaje: Mensaje)` | C  | fecha: DateTime, mensaje: Mensaje          | bool    | Programar |



---

## 3 Relación con otros artefactos del diseño

> Esta sección documenta la **trazabilidad** del caso de uso con los demás artefactos del modelo.  
> Cada fila establece una correspondencia entre los elementos de la matriz CLAE y los artefactos donde aparecen.

| Elemento | Artefacto vinculado | Archivo / Referencia URL | Descripción de la relación |
|-----------|--------------------|-----------------------|-----------------------------|
| `identificarDestinatarios()` | Diagrama de Secuencia – 5 | [`diagramas-secuencia-05.png`](../../diagramas/05-diagramas-secuencia/05-enviar-notificacion-enviar-notificaciones-automaticas-exitoso-05.png) | Representado como la primera acción interna del sistema (“identificar destinatarios”). |
| `identificarDestinatarios()` | Tarjeta CRC – Notificación | [`05-tarjeta-crc-notificacion.md`]() | Relacionado con la responsabilidad “Enviar avisos automáticos al usuario”. |
| `determinarCanalEnvio()` | Diagrama de Secuencia – 5 | [`diagramas-secuencia-05.png`](../../diagramas/05-diagramas-secuencia/05-enviar-notificacion-enviar-notificaciones-automaticas-exitoso-05.png) | Aparece como la segunda acción del sistema (“determinar canal de notificación”). |
| `determinarCanalEnvio()` | Diagrama de Clases – 5 (DIP) | [`diagrama-clases-05-dip.png`](../../diagramas/01-diagrama-clases/01-solid-05-dip.png) | Vinculado con el método definido en la clase Notificacion, que implementa la interfaz INotificacion. |
| `componerMensaje()` | Diagrama de Secuencia – 5 | [`diagramas-secuencia-05.png`](../../diagramas/05-diagramas-secuencia/05-enviar-notificacion-enviar-notificaciones-automaticas-exitoso-05.png) | Aparece como la tercera operación interna del sistema (“componer mensajes para destinatarios”). |
| `componerMensaje()` | Tarjeta CRC – Notificación | [`05-tarjeta-crc-notificacion.md`](../../herramientas-agile/tarjetas-crc/05-tarjeta-crc-notificacion.md) | Asociado con la propiedad “mensaje” y la responsabilidad de informar cambios relevantes. |
| `enviarNotificacion()` | Diagrama de Secuencia – 5 | [`diagramas-secuencia-05.png`](../../diagramas/05-diagramas-secuencia/05-enviar-notificacion-enviar-notificaciones-automaticas-exitoso-05.png) | Representado como el mensaje del sistema al “Servicio de Notificaciones”. |
| `enviarNotificacion()` |  Diagrama de Clases – 5 (DIP) | [`diagrama-clases-05-dip.png`](../../diagramas/01-diagrama-clases/01-solid-05-dip.png) | Corresponde a la operación definida en la interfaz e implementada por la clase concreta. | 
| `registrarEnvio()` | Diagrama de Secuencia – 5 | [`diagramas-secuencia-05.png`](../../diagramas/05-diagramas-secuencia/05-enviar-notificacion-enviar-notificaciones-automaticas-exitoso-05.png) | Representado como la acción “registrar historial de notificaciones”. |
| `registrarEnvio()` | Tarjeta CRC – Notificación | [`05-tarjeta-crc-notificacion.md`](../../herramientas-agile/tarjetas-crc/05-tarjeta-crc-notificacion.md) | Asociado con la responsabilidad de “Programar fecha y hora de envío”. |

---

## 4 Issues e inconsistencias detectadas

> Registrar cualquier diferencia encontrada entre esta matriz y los artefactos relacionados.


| URL | Descripción de la inconsistencia | Artefacto relacionado | Acción correctiva | Estado |
|-----|----------------------------------|------------------------|-------------------|:------:|
| [#60](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/60) | El método `registrarEnvio()` no tiene declarado su tipo de operación (C/L/A/E) en el diagrama de clases. | Diagrama de Clases – 5 (DIP) | Declarar el tipo de operación según sintaxis UML. | Pendiente |
| [#60](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/60) | El método `componerMensaje()` no figura explícitamente en la interfaz `INotificacion`. | Diagrama de Clases – 5 (DIP) | Agregar el método `componerMensaje()` en la interfaz `INotificacion`. | Pendiente |
| [#60](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/60) | No se muestra relación entre la clase Proyecto y la notificación, aunque se usan sus datos. | Diagrama de Clases – 5 (DIP) | Incorporar método `obtenerDatosProyecto()` o una asociación directa con Notificación. | Pendiente |
| [#60](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/60) | La interfaz `INotificacion` define `programarNotificacion()`, pero no se utiliza en UC5. | Diagrama de Clases – 5 (DIP) | Evaluar eliminarlo o integrarlo como flujo alternativo (notificaciones diferidas). | Pendiente |
| [#61](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/61) | En la tarjeta CRC de Notificación no se menciona la responsabilidad de registrar historial. | Tarjeta CRC – Notificación | Añadir responsabilidad “Registrar historial de envío de notificaciones”. | Pendiente |
| [#62](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/62) | El diagrama de secuencia no representa el paso “Determinar canal de envío”. | Diagrama de Secuencia – 5 | Agregar interacción con el módulo/actor que gestiona los canales de envío. | Pendiente |


**Estados posibles:** Abierto / Pendiente / Resuelto

---
