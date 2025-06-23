| ID  | Historia de Usuario                         | Impacto | Complejidad | Tiempo (días) | Prioridad | Riesgos / Dependencias                                           |
|-----|---------------------------------------------|---------|-------------|----------------|-----------|------------------------------------------------------------------|
| HU1 | Crear oferta de empleo                      | 🟢 Alto | 2           | 3              | 1         | Base del sistema; dependencia de HU2, HU6                        |
| HU2 | Publicar oferta en portales externos        | 🟢 Alto | 4           | 5              | 2         | Depende de HU1; riesgo de integración con APIs externas          |
| HU3 | Cribar y puntuar candidatos                 | 🟢 Alto | 3           | 4              | 2         | Depende de HU6; posible ambigüedad en criterios de evaluación    |
| HU4 | Programar entrevistas                       | 🟡 Medio| 3           | 4              | 3         | Depende de HU3; integración con calendarios                      |
| HU5 | Evaluar entrevistas                         | 🟡 Medio| 2           | 2              | 4         | Depende de HU4                                                   |
| HU6 | Aplicar a oferta                            | 🟢 Alto | 3           | 3              | 1         | Depende de HU1; incluye validaciones y subida de CVs             |
| HU7 | Recibir notificaciones y citas              | 🟡 Medio| 3           | 4              | 3         | Depende de HU4 y HU6; afecta experiencia del candidato           |
