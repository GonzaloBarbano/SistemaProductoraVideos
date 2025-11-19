# Matriz CLAE (CRUD) – [cambiar-estado-etapa]

**Proyecto:** Sistema de Gestión de Proyectos Audiovisuales  
**Caso de Uso:** [CUx - cambiar-estado-etapa]  

---

## 1 Tabla CLAE

> **Estructura:**  
> - **Filas:** Actividades internas del caso de uso (acciones o pasos del flujo).  
> - **Columnas:** Clases del sistema involucradas.  
> - **Celdas:** Letras **C**, **L**, **A**, **E** según la operación que se realiza sobre la clase.  
> - Si no aplica, dejar la celda vacía.  

|Actividad / Clase                  | Responsable de Etapa | Coordinador / Productor | asistente de Producción | Servicio de Notificaciones  |
|-----------------------------------|:--------------------:|:-----------------------:|:-----------------------:|:---------------------------:|
| Validar Reglas de Negocio         |         L            |          L              |                         |                             |
| Alertar Posible Retraso           |         C            |                         |                         |              C              |
| Registrar Auditoría               |                      |          C              |                         |              L              |
| Registrar Comentarios             |                      |          L              |           C             |                             |
| Adjuntar Links a Material         |                      |          L              |           C             |                             |
| Enviar Notificaciones Automáticas |         L            |          L              |                         |              C              |
> **Leyenda:**  
> **C**: Crear – **L**: Leer/Listar – **A**: Actualizar – **E**: Eliminar  

---

## 2 Métodos identificados

> Los métodos se derivan directamente de las operaciones (C/L/A/E) marcadas en la tabla.  
> Cada método deberá existir en la clase correspondiente del **diagrama de clases**, y reflejarse en su **Tarjeta CRC** y en el **diagrama de secuencia** del caso de uso.


| Clase                    | Método                                                     | Tipo | Parámetros                       | Retorno | Actividad asociada |
|--------------------------|-----------------------------------------------------------|------|----------------------------------|---------|---------------------|
| Responsable de Etapa     | `validarReglasNegocio(etapa: Etapa, nuevoEstado: Estado)` | L    | etapa: Etapa, nuevoEstado: Estado | bool    | Validar reglas antes del cambio |
| Responsable de Etapa     | `actualizarEstado(etapa: Etapa, nuevoEstado: Estado)`     | A    | etapa: Etapa, nuevoEstado: Estado | bool    | Cambiar estado |
| Coordinador/Productor    | `registrarAuditoria(usuario: Usuario, etapa: Etapa)`      | C    | usuario: Usuario, etapa: Etapa    | bool    | Registrar auditoría |
| Asistente de Producción  | `registrarComentario(etapa: Etapa, texto: string)`         | C    | etapa: Etapa, texto: string       | bool    | Registrar comentarios |
| Asistente de Producción  | `adjuntarLink(etapa: Etapa, url: string)`                 | C    | etapa: Etapa, url: string         | bool    | Adjuntar material |
| Servicio Notificaciones  | `enviarNotificacion(destinatario: Usuario, mensaje: Mensaje)` | C | destinatario: Usuario, mensaje: Mensaje | bool | Enviar aviso |
| Servicio Notificaciones  | `registrarEnvio(etapa: Etapa, estado: Estado)`              | C    | etapa: Etapa, estado: Estado       | bool    | Registrar historial |
| Servicio Notificaciones  | `programarEnvio(fecha: DateTime, mensaje: Mensaje)`        | L    | fecha: DateTime, mensaje: Mensaje | bool    | Programar envío |

---

## 3 Relación con otros artefactos del diseño

> Esta sección documenta la **trazabilidad** del caso de uso con los demás artefactos del modelo.  
> Cada fila establece una correspondencia entre los elementos de la matriz CLAE y los artefactos donde aparecen.

| Elemento | Artefacto vinculado | Archivo / Referencia URL | Descripción de la relación |
|-----------|--------------------|-----------------------|-----------------------------|
| `validarReglasNegocio()` | Tarjeta CRC – responsableDelProyecto | [`04-tarjeta-crc-responsableDelProyecto.md`](../../herramientas-agile/tarjetas-crc/01-tarjeta-crc-proyecto.md) | Figura como responsabilidad: “Autoriza y controla el inicio de las etapas”. |
| `validarReglasNegocio()` | Diagrama de Secuencia – 4 | [`diagramas-secuencia-04.png`](../../diagramas/05-diagramas-secuencia/05-cambiar-estado-etapa-cambiar-estado-de-etapa-exitoso-04.png) | Representa la validación de reglas antes del cambio de estado. |
| `actualizarEstadoEtapa()` | Diagrama de Secuencia – 4 | [`diagramas-secuencia-04.png`](../../diagramas/05-diagramas-secuencia/05-cambiar-estado-etapa-cambiar-estado-de-etapa-exitoso-04.png) | Se ejecuta cuando el Responsable confirma el nuevo estado de la etapa. |
| `registrarAuditoria()` | Tarjeta CRC – Administrador | [`06-tarjeta-crc-administrador.md`](../../herramientas-agile/tarjetas-crc/06-tarjeta-crc-administrador.md) | Definido como responsabilidad de registrar eventos y auditorías. |
| `registrarComentario()` | Tarjeta CRC – Asistente | [`09-tarjeta-crc-asistente.md`](../../herramientas-agile/tarjetas-crc/09-tarjeta-crc-asistente.md) | Figura como responsabilidad de registrar observaciones. |
| `adjuntarLink()` | Tarjeta CRC – Asistente | [`09-tarjeta-crc-asistente.md`](../../herramientas-agile/tarjetas-crc/09-tarjeta-crc-asistente.md) | Se corresponde con la responsabilidad de adjuntar material de apoyo. |
| `enviarNotificacion()` | Diagrama de Secuencia – 4 | [`diagramas-secuencia-04.png`](../../diagramas/05-diagramas-secuencia/05-cambiar-estado-etapa-cambiar-estado-de-etapa-exitoso-04.png) | Refleja el envío automático de una notificación al Coordinador. |
| `registrarEnvio()` | Tarjeta CRC – notificacion | [`05-tarjeta-crc-notificacion.md`](../../herramientas-agile/tarjetas-crc/05-tarjeta-crc-notificacion.md) | Figura como responsabilidad: “Registrar el historial de envíos automáticos”. |
| `registrarEnvio()` | Diagrama de Actividad – 4 | [`diagramas-secuencia-04.png`](../../diagramas/05-diagramas-secuencia/05-cambiar-estado-etapa-cambiar-estado-de-etapa-exitoso-04.png) | Se visualiza como acción “Registrar envío en historial”. |

---

## 4 Issues e inconsistencias detectadas

> Registrar cualquier diferencia encontrada entre esta matriz y los artefactos relacionados.

| URL | Descripción de la inconsistencia | Artefacto relacionado | Acción correctiva | Estado |
|----|----------------------------------|------------------------|-------------------|:------:|
| URL | Descripción de la inconsistencia | Artefacto relacionado | Acción correctiva | Estado |
|----|----------------------------------|------------------------|-------------------|:------:|
| [#55](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/55) | El método `validarReglasNegocio()` está en la CLAE pero no figura en la Tarjeta CRC del Responsable de Etapa. | Tarjeta CRC – Responsable de Etapa | Agregar responsabilidad: “Validar reglas de negocio antes de cambiar el estado”. | Pendiente |
| [#56](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/56) | El método `alertarPosibleRetraso()` aparece en la CLAE pero no está en la CRC del Coordinador/Productor. | Tarjeta CRC – Coordinador/Productor | Incluir operación vinculada al monitoreo del avance de etapas. | Pendiente |
| [#56](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/56) | En la CRC del Administrador se menciona “Designar responsables”, pero no existe ese método en la CLAE de UC4. | Tarjeta CRC – Administrador | Verificar si pertenece a otro caso de uso o agregar referencia en la matriz. | Pendiente |
| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57) | No se representa `alertarPosibleRetraso()` en el diagrama de secuencia. | Diagrama de Secuencia – 4 | Agregar fragmento `alt` que muestre alerta por retraso. | Pendiente |
| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57) | La actividad “Registrar Auditoría” existe en la CLAE pero no está en el diagrama de secuencia. | Diagrama de Secuencia – 4 | Incluir mensaje interno `registrarAuditoria()`. | Pendiente |
| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57) | “Registrar Auditoría” tampoco aparece en el diagrama de actividad. | Diagrama de Actividad – 4 | Agregar acción antes del envío de notificación. | Pendiente |
| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57) | Falta el mensaje `adjuntarLinksMaterial()` en el diagrama de secuencia. | Diagrama de Secuencia – 4 | Incorporar mensaje desde Asistente de Producción. | Pendiente |
| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57) | El diagrama destruye `ServicioNotificaciones`, pero la clase es persistente. | Diagrama de Secuencia – 4 | Eliminar símbolo `destroy` o aclarar instancia temporal. | Pendiente |
| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57) | No se verifica permisos antes del cambio de estado. | Diagrama de Actividad – 4 | Agregar `verificarPermisos(actor)` antes de validar reglas. | Pendiente |
| [#58](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/58) | Falta responsabilidad sobre comentarios en CRC del Asistente. | Tarjeta CRC – Asistente | Añadir responsabilidad “Registrar y gestionar comentarios”. | Pendiente |
| [#59](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/59) | Inconsistencia en nombre "Notificacion" vs "Servicio de Notificaciones". | CRC / Diagramas | Unificar nomenclatura en todos los artefactos. | Pendiente |


**Estados posibles:** Abierto / Pendiente / Resuelto

---
