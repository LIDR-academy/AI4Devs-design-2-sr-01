# ATS — Resumen de User Stories

> Priorización basada en criterios de valor, urgencia, dependencias, coste, riesgos, feedback y madurez tecnológica.

| User Persona   | ID  | Descripción                                                                                                                                                                    | Esfuerzo total (h) | Prioridad |
| -------------- | --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------ | --------- |
| Reclutador     | R1  | Dado un pipeline de una vacante, cuando agrego/quito/reordeno etapas y muevo candidatos con drag-and-drop, entonces el pipeline se actualiza y se registran eventos/auditoría. | 16.5               | Alta      |
| Reclutador     | R2  | Dada una vacante lista, cuando publico en múltiples portales, entonces cada portal devuelve estado y las aplicaciones guardan `source` correcto.                               | 15.0               | Media     |
| Reclutador     | R3  | Dado un cambio de etapa, cuando el candidato entra a una etapa con automatización, entonces se envía la plantilla correspondiente y queda rastro en EventLog.                  | 15.5               | Media     |
| Hiring Manager | H1  | Dado un candidato, cuando completo el scorecard con campos requeridos, entonces se guarda feedback y se consolida multi‑rol con autor y fecha.                                 | 14.0               | Alta      |
| Hiring Manager | H2  | Dado OAuth de calendario conectado, cuando propongo horarios y hay conflictos, entonces recibo slots válidos/sugerencias y se envían invitaciones tentativas.                  | 15.5               | Alta      |
| Hiring Manager | H3  | Dada una oferta ‘pending’, cuando los aprobadores autorizan y el candidato acepta, entonces la oferta pasa a ‘approved’ y la vacante queda ‘closed’ con KPIs actualizados.     | 14.5               | Media     |
| Entrevistador  | I1  | Dado un interview kit, cuando completo mi evaluación y cumplo requeridos, entonces se guarda y participa del consolidado multi‑entrevistador.                                  | 14.5               | Media     |
| Entrevistador  | I2  | Dado mi rol, cuando accedo al interview kit de un candidato, entonces veo sólo datos necesarios según RBAC/tenant y con historial de cambios.                                  | 13.0               | Media     |
| Entrevistador  | I3  | Dada mi disponibilidad, cuando acepto/declino invitaciones o cambia la agenda, entonces se actualizan estados y notificaciones con auditoría.                                  | 13.5               | Media     |
| Candidato      | C1  | Dado que subo mi CV, cuando el parser pre‑llena el formulario con baja confianza en algunos campos, entonces debo confirmar antes de enviar la aplicación.                     | 13.0               | Alta      |
| Candidato      | C2  | Dada mi postulación, cuando consulto el portal, entonces veo la etapa actual, el timeline y recibo notificaciones por cambios.                                                 | 15.0               | Alta      |
| Candidato      | C3  | Dado un set de slots firmados, cuando elijo uno válido, entonces se bloquea en agendas y recibo confirmación; puedo cancelar dentro de la ventana permitida.                   | 15.0               | Media     |
| Admin/RRHH Ops | A1  | Dado SSO/Auth0, cuando un usuario inicia sesión y tiene rol por tenant, entonces se aplica RBAC por recurso y queda auditado.                                                  | 15.0               | Alta      |
| Admin/RRHH Ops | A2  | Dado el Centro de Integraciones, cuando conecto Slack/webhooks/portales y configuro branding, entonces veo estado de salud y se aplica el tema en portal/emails.               | 16.0               | Media     |
| Admin/RRHH Ops | A3  | Dado el catálogo de eventos, cuando defino reglas con prioridad y plantillas versionadas, entonces el motor ejecuta idempotente y reporta conflictos.                          | 16.0               | Media     |
| Analista/BI    | B1  | Dado el dashboard de funnel, cuando aplico filtros y exporto, entonces veo KPIs recalculados y descargo CSV con diccionario de columnas.                                       | 14.5               | Media     |
| Analista/BI    | B2  | Dadas reglas de umbral, cuando una métrica se desvía, entonces se dispara alerta (email/Slack) con historial y posibilidad de silenciamiento.                                  | 15.0               | Baja      |
| Analista/BI    | B3  | Dadas campañas con UTM, cuando genero atribución y ejecuto un A/B, entonces obtengo first/last‑touch, lineal y recomendación con significancia.                                | 15.5               | Baja      |

Tickets de trabajo

[Ver desglose de tickets de trabajo por US](/LTI-IF/ats_tickets_md/README.md)
