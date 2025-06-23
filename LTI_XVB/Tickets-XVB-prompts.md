Genera los Tickets de trabajo de la história de usuario HU1. Aterrízalos técnicamente, tal y como se hace en las reuniones de planificación.


---

Estima el esfuerzo de los tickets usando la metología poker

---

Perfecto. A continuación aplico la **estimación por *Planning Poker*** a los tickets de la historia HU1. Esta técnica consiste en asignar puntos de historia (Story Points) basados en la **complejidad, incertidumbre y esfuerzo relativo**, usando la secuencia de Fibonacci modificada:

> **Valores típicos**: 0, 0.5, 1, 2, 3, 5, 8, 13, 20, etc.

---

## 🎴 Estimación de los Tickets HU1 con Planning Poker

```markdown
| ID     | Título del Ticket                                              | Estimación (Story Points) | Justificación                                                                 |
|--------|----------------------------------------------------------------|----------------------------|--------------------------------------------------------------------------------|
| HU1-1  | Diseñar modelo de datos JobOffer                               | 2                          | Modelo sencillo pero esencial; baja incertidumbre                             |
| HU1-2  | Crear endpoint REST para crear y guardar una oferta            | 3                          | Requiere lógica de negocio y pruebas básicas                                  |
| HU1-3  | Crear formulario de frontend para nueva oferta                 | 5                          | Implica diseño visual, validación y pruebas de UX                             |
| HU1-4  | Conectar formulario con API REST                               | 2                          | Tarea de integración bien definida                                            |
| HU1-5  | Mostrar validaciones y errores en el frontend                  | 2                          | Lógica visual con reglas claras; impacto en UX                                |
| HU1-6  | Guardar como borrador o publicar                               | 2                          | Aumenta lógica condicional y ramificaciones de estado                         |
| HU1-7  | Pruebas unitarias de creación de ofertas                       | 2                          | Bajo esfuerzo, pero requiere detalle en validaciones                          |
| HU1-8  | Pruebas de integración del flujo de creación de ofertas       | 3                          | Requiere entorno completo, pruebas end-to-end                                 |
| HU1-9  | Documentar API REST de creación de ofertas                     | 1                          | Tarea rutinaria con plantilla establecida                                     |
```

---

### 🔍 Resumen:

* Total puntos estimados: **22 Story Points**
* Historia relativamente ligera en complejidad, pero crítica en flujo.
* Los tickets HU1-3 (frontend completo) y HU1-8 (integración) son los más costosos.

¿Quieres que integre esta tabla en el documento `.md` ya generado? También puedo preparar un gráfico de burndown o sugerirte cómo repartir esta historia en varios sprints.

