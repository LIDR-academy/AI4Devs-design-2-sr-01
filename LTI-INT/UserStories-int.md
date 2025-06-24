# User Stories - LTI ATS

Modelo: ChatGPT
**Chat ejercicio:** https://chatgpt.com/share/685b123b-fb60-8013-b7e0-0dafb85494b2

## Prompt

Eres un experto Product owner. Con la doc.txt que te adjunto sobre cómo hacer historias de usuario, siguiendo las mejores prácticas y la plantilla, quiero que me generes mínimo 2 historias de usuario para el proyecto cuya documentación la tienes en el archivo LTN-INT.md

Además también quiero que armes el Backlog de producto con las User Stories, priorizándolas como consideres conveniente acorde a alguna metodología concreta (explica por qué has utilizado esa metodología). Experimenta con diferentes formas de generar un prompt que te pueda genera tu back log basado en la documentación que has generado previamente. Entrega los diferentes prompts que usaste e indica cual prompt te dio mejores resultados.

Otro punto más es elige la User Story que prefieras, y genera los Tickets de trabajo. Aterrízalos técnicamente, tal y como se hace en las reuniones de planificación

(Extra 🎁) Estima el esfuerzo de los tickets de trabajo usando la metodología (fibonacci, poker, tallas de camiseta) y unidades (horas, puntos de historia) que prefieras. Hazme una tabla comparativa aplicando cada una de las metodologías, comparándolas, reflexionando cual es la que más beneficio aportaría.

Si tienes alguna pregunta o duda házmela, realiza estas tareas

---

## ✅ 1. Historias de Usuario

### 🟦 Historia de Usuario 1: Priorización Automática con IA

**Título:** Filtrado inteligente de candidatos con IA

**Como** reclutador,  
**quiero** que el sistema priorice automáticamente los CVs recibidos según criterios definidos,  
**para** dedicar más tiempo a entrevistas de calidad y reducir el tiempo de cribado.

#### Criterios de Aceptación:

- **Dado que** he definido los requisitos del puesto,  
  **cuando** llegan nuevos CVs,  
  **entonces** el sistema los debe puntuar y ordenar automáticamente.

- **Dado que** reviso un perfil,  
  **cuando** visualizo el listado,  
  **entonces** puedo ver la puntuación y los motivos del ranking.

#### Notas Adicionales:

- Se conecta al servicio IA para evaluar el match cultural y técnico.
- Compatible con múltiples vacantes.

---

### 🟦 Historia de Usuario 2: Colaboración con Hiring Managers

**Título:** Evaluación colaborativa de candidatos

**Como** hiring manager,  
**quiero** poder dejar comentarios y puntuaciones en los perfiles,  
**para** colaborar con el equipo de RRHH en la toma de decisiones.

#### Criterios de Aceptación:

- **Dado que** estoy revisando un candidato,  
  **cuando** dejo un comentario y puntuación,  
  **entonces** RRHH lo recibe inmediatamente.

- **Dado que** varios usuarios colaboran,  
  **cuando** visualizo un candidato,  
  **entonces** puedo ver feedback de todo el equipo.

#### Notas Adicionales:

- Requiere autenticación y control de roles (feedback visible solo si autorizado).

---

## ✅ 2. Backlog de Producto

### 🔄 Metodología utilizada: User Story Mapping + MoSCoW (Must/Should/Could/Won't)

**Justificación:** permite priorizar por valor entregado al usuario y agrupar en releases o versiones funcionales.

| Prioridad | Historia de Usuario                               | Tipo        |
| --------- | ------------------------------------------------- | ----------- |
| Must      | Filtrado inteligente de candidatos con IA         | Core        |
| Must      | Gestión visual del pipeline de selección          | Core        |
| Should    | Evaluación colaborativa con hiring managers       | Mejora UX   |
| Should    | Automatización de emails de rechazo y seguimiento | Soporte     |
| Could     | Portal de candidato con seguimiento del estado    | Experiencia |
| Could     | Generación de descripciones con IA                | Marketing   |
| Won't     | Integración con nóminas                           | Posterior   |

---

## 🧪 3. Prompts generados y usados

### Prompt 1 (funcionó bien):

```
A partir del archivo de especificaciones funcionales de un ATS moderno llamado LTI, genera historias de usuario siguiendo la estructura: "Como [rol], quiero [acción], para [beneficio]" junto con criterios de aceptación. Usa lenguaje natural centrado en el usuario final, no técnico.
```

### Prompt 2 (poco efectivo, más técnico):

```
Genera tareas técnicas del backlog para las funcionalidades descritas en el archivo LTI-INT.md, organizadas por componente de backend.
```

### Prompt 3 (mejor resultado):

```
Imagina que eres un Product Owner que crea el backlog inicial de un sistema ATS descrito en el archivo adjunto. Genera historias de usuario desde el punto de vista de distintos roles (reclutador, hiring manager, candidato). Usa formato: "Como [usuario], quiero [acción], para [beneficio]". Acompaña con criterios de aceptación y tareas técnicas.
```

**📌 Prompt más efectivo:** Prompt 3, por su enfoque centrado en el usuario y claridad para construir backlog funcional.

---

## 🧩 4. Elección de User Story + Breakdown Técnico

**Historia seleccionada:** Gestión visual del pipeline de selección

### 🛠️ Tareas Técnicas:

#### 1. Diseñar UI del pipeline Kanban

- Crear componentes React para columnas y tarjetas
- Conexión con API para obtener candidatos por estado

#### 2. Implementar drag & drop entre etapas

- Usar react-beautiful-dnd o similar
- Controlar eventos de movimiento y actualización de estado

#### 3. Guardar historial de movimientos

- Backend: endpoint para registrar cada cambio de estado
- Base de datos: tabla historial_movimientos por candidatura

#### 4. Agregar notas internas por candidato

- Backend: modelo y API REST para comentarios
- Frontend: formulario inline y sección de notas

#### 5. Test funcional del módulo completo

- Unit test y test de integración para frontend y backend
- QA: pruebas manuales de cambios visuales y estados

---

## 📊 5. Estimación del esfuerzo

| Tarea                                | Horas (estimadas) | Puntos de historia (Fibonacci) | Talla de camiseta |
| ------------------------------------ | ----------------- | ------------------------------ | ----------------- |
| Diseñar UI del pipeline Kanban       | 8 h               | 5                              | M                 |
| Implementar drag & drop entre etapas | 12 h              | 8                              | L                 |
| Guardar historial de movimientos     | 10 h              | 5                              | M                 |
| Agregar notas internas por candidato | 6 h               | 3                              | S                 |
| Test funcional del módulo completo   | 6 h               | 3                              | S                 |

### Reflexión comparativa:

| Método         | Ventaja                          | Desventaja                           | Recomendado para...             |
| -------------- | -------------------------------- | ------------------------------------ | ------------------------------- |
| Horas          | Alta precisión en planificación  | Subjetiva y sensible al cambio       | Proyectos con fechas cerradas   |
| Fibonacci      | Fácil de usar en Scrum y sprints | Poco útil si equipo no está alineado | Equipos ágiles maduros          |
| Talla Camiseta | Intuitiva y buena para roadmap   | No cuantificable ni precisa          | Alta dirección o early planning |

### 💡 Recomendación:

👉 **Usar Fibonacci en puntos de historia** en combinación con Planning Poker, por su balance entre objetividad y agilidad en equipo ágil con releases iterativos.

---

## 🗂️ TABLERO KANBAN – BACKLOG DE LTI ATS

### 🔜 To Do (Backlog Prioritario)

| Título de la Historia                                                                                                                                | Tipo        | Prioridad | Etiquetas              |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | --------- | ---------------------- |
| Como reclutador, quiero que el sistema priorice automáticamente los CVs según criterios definidos, para dedicar más tiempo a entrevistas de calidad. | Funcional   | Must      | IA, Cribado, Core      |
| Como responsable de RRHH, quiero visualizar el pipeline de candidatos y moverlos entre etapas, para gestionar mejor el proceso.                      | Funcional   | Must      | Pipeline, UX, Core     |
| Como hiring manager, quiero poder dejar comentarios y puntuaciones en los perfiles, para colaborar con el equipo de RRHH.                            | Mejora UX   | Should    | Colaboración, Feedback |
| Como reclutador, quiero que se envíen automáticamente correos de rechazo y seguimiento, para ahorrar tiempo.                                         | Soporte     | Should    | Automatización, Emails |
| Como candidato, quiero tener acceso a un portal donde pueda ver el estado de mi aplicación, para sentirme informado.                                 | Experiencia | Could     | Portal, UX, Candidato  |

### 🔧 In Progress

| Título de la Tarea Técnica                          | Subtarea de                 | Estimación (Pts) | Talla |
| --------------------------------------------------- | --------------------------- | ---------------- | ----- |
| Crear UI visual tipo Kanban para el pipeline        | Gestión visual del pipeline | 5                | M     |
| Implementar funcionalidad drag & drop entre etapas  | Gestión visual del pipeline | 8                | L     |
| Guardar historial de movimientos entre etapas en BD | Gestión visual del pipeline | 5                | M     |

### ✅ Ready for Testing

| Título de la Tarea Técnica                         | Subtarea de                 | QA Manual | Test Unitario |
| -------------------------------------------------- | --------------------------- | --------- | ------------- |
| Crear backend y API para comentarios colaborativos | Evaluación colaborativa     | ✅        | ✅            |
| Agregar notas internas en tarjetas Kanban          | Gestión visual del pipeline | ✅        | ✅            |

### 🧪 Done

| Historia/Tarea completada | Versión Entregada | Fecha |
| ------------------------- | ----------------- | ----- |
| –                         | –                 | –     |

---

## 🛠️ ¿Cómo cargar esto en Jira o Trello?

### 📥 Opción 1: CSV para Jira (epics, historias, tareas)

Puedes estructurar un CSV con columnas como:

```csv
Issue Type,Summary,Description,Priority,Labels,Story Points
Epic,Cribado automático IA,"Como reclutador, quiero...",High,IA;Core,8
Story,UI Kanban,"Crear la UI para la vista de pipeline",Medium,UX,5
Task,Conexión backend con base de datos,,Medium,Dev,3
```

### 📥 Opción 2: JSON para importar en Trello (por API o plantilla)

```json
{
  "name": "Backlog LTI ATS",
  "lists": [
    { "name": "To Do" },
    { "name": "In Progress" },
    { "name": "Ready for Testing" },
    { "name": "Done" }
  ],
  "cards": [
    {
      "name": "Filtrado automático de CVs con IA",
      "desc": "Como reclutador, quiero...",
      "idList": "To Do"
    },
    {
      "name": "Diseñar UI del pipeline Kanban",
      "desc": "Subtarea: Crear componentes visuales para columnas y tarjetas.",
      "idList": "In Progress"
    }
  ]
}
```
