# ATS-R1-01 — Modelo “Stage” por vacante

**Prioridad:** Alta  
**Esfuerzo estimado:** 3.0 h

## Descripción
Crear esquema `stages` por `job_id` con orden y metadatos de automatizaciones vinculadas.

## Criterios de aceptación
- se puede crear/listar/borrar/ordenar etapas por vacante
- constraints de orden únicos por `job_id`

## Tareas técnicas
- migración DB
- repo + DTO
- endpoints GET/POST/DELETE
- tests unit


**Notas:** Cuidar idempotencia al reordenar.
