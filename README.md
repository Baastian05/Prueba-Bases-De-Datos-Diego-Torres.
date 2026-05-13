# Prueba Práctica Avanzada - Oracle SQL

**Estudiante:** Diego Sebastian Torres Caluña
**Escenario:** N° 25 - Plataforma Streaming
**Regla de Integridad:** RESTRICT
**Institución:** Universidad Técnica de Ambato - FIS

---

## 1. Justificación del Modelo Lógico Simplificado

Para el desarrollo de esta prueba, se optó por un modelo simplificado basado en las entidades críticas del escenario (**USUARIO, PELICULA, SUSCRIPCION, VISUALIZACION, PLAN**). Esta decisión se fundamenta en:

* **Enfoque en Entidades Críticas:** Permite demostrar el dominio de relaciones complejas y restricciones de integridad sin ruido innecesario, centrándose en el flujo principal del negocio.
* **Eficiencia en Tiempo:** Facilita el desarrollo manual y la implementación de scripts SQL dentro del límite de 90 minutos, sin comprometer la lógica técnica.
* **Coherencia DDL/DML:** Asegura una trazabilidad clara entre el diseño, la creación de tablas y la manipulación de datos, facilitando la validación de la integridad referencial.
* **Claridad Pedagógica:** Permite visualizar rápidamente la jerarquía de llaves primarias y foráneas, esencial para la aplicación de la regla **RESTRICT**.

---

## 2. Análisis Profesional (Parte 4)

### 2.1. Atomicidad (Propiedad ACID)
Es el principio de **"todo o nada"**. Establece que una transacción debe ejecutarse como una unidad única e indivisible.
* **Funcionamiento:** Si todas las operaciones tienen éxito, se aplica un `COMMIT`. Si una sola falla, se realiza un `ROLLBACK` para volver al estado original.
* **Propósito:** Evitar que la base de datos quede en un estado inconsistente o con datos parciales.

### 2.2. DELETE sin WHERE
Es una instrucción crítica que elimina la totalidad de los registros de una tabla de forma indiscriminada.
* **Riesgo:** Al no filtrar por una condición específica, se pierde toda la información de la entidad.
* **Diferencia técnica:** A diferencia de `TRUNCATE`, permite revertir la operación con un `ROLLBACK` (si no se ha confirmado), pero consume más recursos del sistema al generar registros de log.

### 2.3. ON DELETE CASCADE vs. RESTRICT
Son reglas de integridad referencial que definen el comportamiento del sistema ante la eliminación de datos vinculados.
* **ON DELETE CASCADE:** Automatiza la limpieza eliminando registros "hijos" cuando se borra un registro "padre".
* **RESTRICT (Aplicada en este proyecto):** Bloquea la eliminación del registro "padre" si detecta que existen registros relacionados, garantizando que no existan datos huérfanos y protegiendo el historial de la plataforma.

---
*Este repositorio contiene el desarrollo manual, diagramas y scripts SQL correspondientes a la evaluación de la asignatura de Bases de Datos.*
