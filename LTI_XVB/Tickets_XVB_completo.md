# Diseñar modelo de datos JobOffer

## 2. Descripción Detallada
**Propósito:** Definir la estructura de la entidad principal del sistema: oferta de empleo. Esta entidad servirá como base para el resto del proceso de selección.
**Detalles Específicos:**
- Campos: id, título, descripción, requisitos, localización, estado (borrador/publicado), fechas.
- Uso de anotaciones JPA (@Entity, @Id, @Column...)

## 3. Criterios de Aceptación
- El modelo debe compilar sin errores.
- Debe estar mapeado correctamente a la base de datos.
- Debe contemplar validaciones básicas (longitud máxima, requeridos).

## 4. Prioridad
- Alta

## 5. Estimación de Esfuerzo
- 1 día

## 6. Asignación
- Equipo Backend

## 7. Etiquetas o Tags
- backend, entidad, modelo-datos

## 8. Comentarios y Notas
- Asegurarse de dejar espacio para campos adicionales (e.g. salario).

## 9. Enlaces o Referencias
- https://hibernate.org/orm/documentation/6.2/

## 10. Historial de Cambios
- 2025-06-23: Creación del ticket.

---

# Crear endpoint REST para crear y guardar una oferta

## 2. Descripción Detallada
**Propósito:** Permitir la creación de nuevas ofertas de empleo mediante una API REST.
**Detalles Específicos:**
- Endpoint: POST /api/joboffers
- Formato JSON, integración con capa de persistencia.

## 3. Criterios de Aceptación
- El endpoint debe aceptar una oferta en formato JSON.
- Debe persistir correctamente la entidad JobOffer.
- Debe devolver un código 201 y el ID creado.

## 4. Prioridad
- Alta

## 5. Estimación de Esfuerzo
- 1 día

## 6. Asignación
- Equipo Backend

## 7. Etiquetas o Tags
- backend, api, rest

## 8. Comentarios y Notas
- Considerar validaciones con Bean Validation.

## 9. Enlaces o Referencias
- https://jakarta.ee/specifications/restful-ws/3.0/

## 10. Historial de Cambios
- 2025-06-23: Creación del ticket.

---

# Crear formulario de frontend para nueva oferta

## 2. Descripción Detallada
**Propósito:** Ofrecer una interfaz gráfica para que los usuarios de RRHH puedan introducir los datos de una nueva oferta.
**Detalles Específicos:**
- Campos: título, descripción, requisitos, localización.
- Debe incluir campos obligatorios con validación visual.

## 3. Criterios de Aceptación
- Formulario visual responsive en el navegador.
- Validaciones en tiempo real (HTML5 o JS).
- Botones para guardar como borrador o publicar.

## 4. Prioridad
- Alta

## 5. Estimación de Esfuerzo
- 1.5 días

## 6. Asignación
- Equipo Frontend

## 7. Etiquetas o Tags
- frontend, formulario, UI

## 8. Comentarios y Notas
- Usar componentes reutilizables si existen.

## 9. Enlaces o Referencias
- https://reactjs.org/docs/forms.html

## 10. Historial de Cambios
- 2025-06-23: Creación del ticket.

---


# Conectar formulario con API REST

## 2. Descripción Detallada
**Propósito:** Integrar el formulario de creación de ofertas con el backend mediante una llamada al endpoint REST.
**Detalles Específicos:**
- Usar `fetch` o biblioteca como `axios`.
- Enviar los datos del formulario como JSON a `/api/joboffers`.
- Mostrar mensajes de confirmación o error según la respuesta.

## 3. Criterios de Aceptación
- El formulario debe enviar correctamente los datos al backend.
- El usuario debe ver un mensaje de éxito si se crea la oferta.
- Los errores de validación o del servidor deben mostrarse al usuario.

## 4. Prioridad
- Alta

## 5. Estimación de Esfuerzo
- 0.5 días

## 6. Asignación
- Equipo Frontend

## 7. Etiquetas o Tags
- frontend, integración, api

## 8. Comentarios y Notas
- Validar bien los formatos antes de enviar.

## 9. Enlaces o Referencias
- https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API

## 10. Historial de Cambios
- 2025-06-23: Creación del ticket.

---

# Mostrar validaciones y errores en el frontend

## 2. Descripción Detallada
**Propósito:** Asegurar una buena experiencia de usuario mostrando mensajes claros de validación y errores.
**Detalles Específicos:**
- Mensajes inline para campos obligatorios.
- Mostrar errores devueltos por la API en una alerta o toast.

## 3. Criterios de Aceptación
- Validaciones en tiempo real antes del envío.
- Mostrar mensajes descriptivos por campo.
- Si hay error del servidor, debe verse claramente.

## 4. Prioridad
- Media

## 5. Estimación de Esfuerzo
- 0.5 días

## 6. Asignación
- Equipo Frontend

## 7. Etiquetas o Tags
- frontend, UX, validación

## 8. Comentarios y Notas
- Alinear con la guía de estilo del producto.

## 9. Enlaces o Referencias
- https://formik.org/docs/guides/validation

## 10. Historial de Cambios
- 2025-06-23: Creación del ticket.

---

# Añadir funcionalidad de “guardar como borrador” o “publicar”

## 2. Descripción Detallada
**Propósito:** Permitir al usuario elegir si guarda la oferta como borrador o la publica directamente.
**Detalles Específicos:**
- Campo `published` en `JobOffer`.
- Dos botones en el formulario: “Guardar” y “Publicar”.

## 3. Criterios de Aceptación
- Si se guarda como borrador, `published = false`.
- Si se publica, `published = true` y se guarda `publishedAt`.
- Comprobación en backend del estado enviado.

## 4. Prioridad
- Media

## 5. Estimación de Esfuerzo
- 0.5 días

## 6. Asignación
- Equipo Backend

## 7. Etiquetas o Tags
- backend, lógica de negocio

## 8. Comentarios y Notas
- Considerar flag `isDraft` en la interfaz de frontend.

## 9. Enlaces o Referencias
- https://www.baeldung.com/jpa-persist-different-entity-states

## 10. Historial de Cambios
- 2025-06-23: Creación del ticket.

---

# Pruebas unitarias de creación de ofertas

## 2. Descripción Detallada
**Propósito:** Verificar que la lógica de persistencia y validación funcione correctamente en el backend.
**Detalles Específicos:**
- Usar JUnit y Mockito.
- Testear caso exitoso, campos vacíos, errores de persistencia.

## 3. Criterios de Aceptación
- Test que valide oferta completa válida.
- Test que falle si campos requeridos están vacíos.
- Cobertura mínima del 80%.

## 4. Prioridad
- Alta

## 5. Estimación de Esfuerzo
- 0.5 días

## 6. Asignación
- Equipo Backend

## 7. Etiquetas o Tags
- test, backend, unitarios

## 8. Comentarios y Notas
- Incluir test para guardar como borrador y publicar.

## 9. Enlaces o Referencias
- https://junit.org/junit5/docs/current/user-guide/

## 10. Historial de Cambios
- 2025-06-23: Creación del ticket.

---

# Pruebas de integración del flujo de creación de ofertas

## 2. Descripción Detallada
**Propósito:** Validar el flujo completo desde el frontend hasta el backend.
**Detalles Específicos:**
- Simular el envío del formulario completo.
- Verificar la creación en la base de datos.

## 3. Criterios de Aceptación
- La oferta aparece en base de datos al enviar el formulario.
- El frontend muestra mensajes de éxito y error correctamente.

## 4. Prioridad
- Alta

## 5. Estimación de Esfuerzo
- 1 día

## 6. Asignación
- QA

## 7. Etiquetas o Tags
- test, integración, end-to-end

## 8. Comentarios y Notas
- Usar Postman/Newman o tests automatizados con Cypress.

## 9. Enlaces o Referencias
- https://docs.cypress.io/

## 10. Historial de Cambios
- 2025-06-23: Creación del ticket.

---

# Documentar API REST de creación de ofertas

## 2. Descripción Detallada
**Propósito:** Añadir la documentación formal del endpoint de creación en el Swagger del proyecto.
**Detalles Específicos:**
- Anotar con `@Operation` y `@ApiResponse`.
- Mostrar ejemplo de solicitud y respuesta.

## 3. Criterios de Aceptación
- Endpoint debe aparecer en Swagger.
- Incluir ejemplos claros y códigos de respuesta.

## 4. Prioridad
- Media

## 5. Estimación de Esfuerzo
- 0.5 días

## 6. Asignación
- Equipo Backend

## 7. Etiquetas o Tags
- documentación, swagger, backend

## 8. Comentarios y Notas
- Usar OpenAPI 3.x

## 9. Enlaces o Referencias
- https://swagger.io/specification/

## 10. Historial de Cambios
- 2025-06-23: Creación del ticket.

---

