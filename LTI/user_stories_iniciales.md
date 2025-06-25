# User Stories Iniciales

## 1. Plantilla Común de User Story

```markdown
- **ID:** US-XX
- **Como** [rol]
- **Quiero** [funcionalidad]
- **Para** [beneficio]
- **Criterios de Aceptación:**
  - **Dado** [contexto]
  - **Cuando** [acción]
  - **Entonces** [resultado esperado]
- **Prioridad:** [Must/Should/Could]
```

## 2. Historias Generadas

- **US-01**

  - **Como** Reclutador
  - **Quiero** crear un nuevo candidato con nombre, email y CV
  - **Para** gestionar eficientemente los perfiles de aspirantes
  - **Criterios de Aceptación:**
    - Dado que el reclutador está autenticado
    - Cuando envía un POST a `/candidates` con datos válidos
    - Entonces se crea un candidato y devuelve HTTP 201 con el ID
  - **Prioridad:** Must

- **US-02**

  - **Como** Reclutador
  - **Quiero** listar todos los candidatos con paginación
  - **Para** revisar y filtrar perfiles de manera ordenada
  - **Criterios de Aceptación:**
    - Dado que el reclutador está autenticado
    - Cuando solicita GET `/candidates?page=0&size=10`
    - Entonces recibe una lista de hasta 10 candidatos y metadatos de paginación
  - **Prioridad:** Must

- **US-03**

  - **Como** Reclutador
  - **Quiero** publicar una vacante con título, descripción y requisitos
  - **Para** atraer candidatos adecuados
  - **Criterios de Aceptación:**
    - Dado que el reclutador está autenticado
    - Cuando envía un POST a `/vacancies` con datos válidos
    - Entonces se crea la vacante y devuelve HTTP 201
  - **Prioridad:** Should

- **US-04**

  - **Como** Candidato
  - **Quiero** aplicar a una vacante existente
  - **Para** postularme a ofertas de empleo
  - **Criterios de Aceptación:**
    - Dado que el candidato está autenticado
    - Cuando envía un POST a `/applications` con candidateId y vacancyId
    - Entonces se crea la aplicación y devuelve HTTP 201
  - **Prioridad:** Should

## 3. Product Backlog y Priorización (MoSCoW)

| ID    | Descripción                      | Prioridad | Story Points |
| ----- | -------------------------------- | --------- | ------------ |
| US-01 | Crear candidato                  | Must      | 5            |
| US-02 | Listar candidatos con paginación | Must      | 3            |
| US-03 | Publicar vacante                 | Should    | 5            |
| US-04 | Aplicar candidato a vacante      | Should    | 5            |
| US-05 | Autenticación JWT                | Must      | 8            |

## 4. Experimentación de Prompts

1. **Prompt A:**
   ```text
   Con base en la documentación de implementación de LTI, genera un backlog de producto con historias de usuario usando MoSCoW, incluyendo ID, rol, descripción, criterios de aceptación y prioridad.
   ```
2. **Prompt B:**
   ```text
   Usando el PRD de LTI, crea al menos 5 user stories con plantilla estándar (Como, Quiero, Para, Criterios de aceptación), asigna prioridad y story points.
   ```
3. **Prompt C:**
   ```text
   Genera un product backlog extraído de la documentación inicial de LTI. Cada ítem debe ser una user story completa, priorizada según valor de negocio y estimada en story points.
   ```

**Conclusión:** El **Prompt B** fue el más efectivo, pues especifica claramente la plantilla, el mínimo de historias y la inclusión de prioridad y estimación, lo que generó un formato consistente.

## 5. Desglose de Tareas para US-01: Crear Candidato

**User Story US-01**: Como Reclutador, quiero crear un nuevo candidato con nombre, email y CV, para gestionar eficientemente los perfiles de aspirantes.

### Tickets y Estimaciones

1. **TICKET-101: Backend – Endpoint POST /candidates** (5 SP / 8h)

   - Definir DTO `CandidateRequest` y entidad `Candidate` (1h)
   - Configurar repositorio reactivo (1h)
   - Implementar `CandidateService.create()` (2h)
   - Crear `CandidateController` POST `/candidates` (2h)
   - Añadir validaciones básicas (Bean Validation)

2. **TICKET-102: Frontend – Formulario de creación de candidato** (5 SP / 9h)

   - Componente `CandidateForm.tsx` con campos (1h)
   - Validación de campos (2h)
   - Integración API (2h)
   - Manejo de errores y carga (1h)
   - Pruebas con React Testing Library (2h)

3. **TICKET-103: QA – Pruebas de integración** (3 SP / 4h)

   - Test e2e con Cypress (2h)
   - Validar base de datos (1h)
   - Documentar casos de prueba (1h)

---

*Ubicación en el repositorio:* `LTI-EYMV/UserStories-iniciales.md`

