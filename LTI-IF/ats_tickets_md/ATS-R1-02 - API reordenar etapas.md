# ATS-R1-02 — API reordenar etapas

**Prioridad:** Alta  
**Esfuerzo estimado:** 3.0 h

## Descripción
Endpoint `PATCH /jobs/:id/stages/reorder`.

## Criterios de aceptación
- persiste nuevo orden
- valida colisiones
- registra `EventLog`

## Tareas técnicas
- handler
- validaciones
- evento StageReordered
- tests

