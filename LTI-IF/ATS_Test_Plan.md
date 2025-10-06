# ATS — Plan de Pruebas
Fecha: 2025-10-02

## 1. Objetivo
Asegurar calidad funcional y no funcional del ATS (multitenant, SSO, microservicios) con foco en historias R1–R3, H1–H3, I1–I3, C1–C3, A1–A3, B1–B3. Cobertura desde **smoke** hasta **regresión**, con pruebas de **integración**, **E2E** y **datos**.

## 2. Alcance
- **Funcional**: pipelines, multiposting, automatizaciones, scorecards, agenda, ofertas, portal candidato, SSO/RBAC, integraciones, reglas, dashboards, alertas, atribución y A/B.
- **No funcional**: seguridad (SSO/Auth0, RBAC), rendimiento (p99 endpoints críticos), resiliencia (reintentos, idempotencia), observabilidad y auditoría.

## 3. Fuera de Alcance (fase actual)
- Cargas extremas (> P95 objetivo) y caos testing profundo.
- Conectores de portales reales en producción (se usa stub/mocks).

## 4. Estrategia de Pruebas
- **Unitarias**: validaciones, mapeos, reglas de negocio, adapters.
- **Integración**: API↔DB, orquestadores, colas/eventos, proveedores externos stub.
- **E2E/UI**: flujos críticos (pipeline DnD, multiposting, agenda, ofertas, portal candidato).
- **Datos/ETL**: materialized views, KPIs, exportaciones, frescura.
- **Seguridad**: RBAC por recurso, enlaces firmados, expiraciones, auditoría.
- **Compatibilidad**: zonas horarias, idiomas, branding por tenant.

## 5. Entornos
- **DEV**: despliegue continuo, datos sintéticos.
- **STAGING**: datos casi reales, claves de prueba para OAuth/Slack.
- **PROD** (observación): feature flags/gradual rollout, métricas y alertas.

## 6. Herramientas
- Testing backend: Jest/Vitest, Supertest; Testcontainers (DB/colas).
- Testing UI: Playwright/Cypress (smoke/regresión).
- Contract tests: Pact (APIs y webhooks).
- Monitoreo y logs: OpenTelemetry, Prometheus, Grafana.
- Gestión: Jira para casos/defectos, Allure/ReportPortal para reportes.

## 7. Criterios de Entrada
- Historias refinadas con criterios de aceptación.
- Endpoints/documentación actualizada.
- Datos de prueba y usuarios por rol/tenant.
- Mocks/credenciales de prueba disponibles.

## 8. Criterios de Salida
- 0 defectos **bloqueantes**.
- ≤ 3 defectos **mayores** abiertos con mitigación/fecha.
- Cobertura mínima: 80% unit, 70% integración en módulos críticos.
- Suite **smoke** estable y verde en 3 ejecuciones consecutivas.
- Pruebas E2E clave verdes (pipeline, agenda, ofertas, portal candidato).

## 9. Gestión de Riesgos
- **Dependencias externas** (OAuth/Calendars/Slack) → usar stubs y reintentos; test resiliencia.
- **Idempotencia/duplicados** en reglas/notificaciones → llaves de dedupe + pruebas de repetición.
- **Zonas horarias** → normalización y pruebas de conversión.
- **Datos personales (PII)** → mínimos necesarios en UI, mascar y auditar accesos.

## 10. Matriz de Trazabilidad (Resumen)
| Feature | Ejemplos de Tickets | Tipos de Prueba |
|---|---|---|
| R1 | ATS-R1-01..05 | Unit, Integración, E2E UI |
| R2 | ATS-R2-01..05 | Unit, Integración, E2E API/UI |
| R3 | ATS-R3-01..05 | Unit, Integración |
| H1 | ATS-H1-01..05 | Unit, UI, Integración |
| H2 | ATS-H2-01..05 | Integración Calendario, E2E |
| H3 | ATS-H3-01..05 | Integración, UI, E2E |
| I1 | ATS-I1-01..05 | Unit, UI |
| I2 | ATS-I2-01..05 | Seguridad/RBAC, UI |
| I3 | ATS-I3-01..05 | Calendario, E2E |
| C1 | ATS-C1-01..05 | API, Seguridad de documentos |
| C2 | ATS-C2-01..05 | API/UI, Notificaciones |
| C3 | ATS-C3-01..05 | API/UI, Calendario |
| A1 | ATS-A1-01..05 | Auth/SSO, Seguridad |
| A2 | ATS-A2-01..05 | Integraciones, Branding |
| A3 | ATS-A3-01..05 | Reglas, Idempotencia |
| B1 | ATS-B1-01..05 | Datos/ETL, UI |
| B2 | ATS-B2-01..05 | Alertas, Notificaciones |
| B3 | ATS-B3-01..05 | Datos, Experimentos |

## 11. Plan de Ejecución
- **Smoke diario**: login SSO, pipeline básico, publicar stub, mover candidato, ver portal.
- **Regresión por release**: suites por feature/tag (`@smoke`, `@regression`).
- **Datos**: verificación de frescura y exportes.
- **Seguridad**: RBAC por recurso, enlaces firmados y expiraciones.

## 12. Entregables
- Reportes de ejecución (CI), evidencias, defectos en Jira, cobertura y paneles de calidad.
