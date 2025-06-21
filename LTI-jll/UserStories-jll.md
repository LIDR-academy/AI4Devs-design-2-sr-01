# Historias de Usuario

## Historia de Usuario 1: Publicar vacantes en LinkedIn

**Título:** Como Responsable de RRHH, quiero publicar vacantes directamente en LinkedIn para atraer candidatos de manera eficiente.

**Descripción:** Esta funcionalidad permitirá a los responsables de RRHH publicar vacantes en LinkedIn desde el sistema LTI, sincronizando automáticamente los datos de la oferta laboral.

**Criterios de Aceptación:**
- Dado que el Responsable de RRHH tiene una vacante creada en el sistema,
  - Cuando selecciona la opción de publicar en LinkedIn,
  - Entonces la vacante se publica correctamente en LinkedIn con todos los datos sincronizados.
- Dado que la publicación en LinkedIn requiere autenticación,
  - Cuando el Responsable de RRHH no ha iniciado sesión en LinkedIn,
  - Entonces el sistema solicita autenticarse antes de publicar.

**Equipo:** Backend, Integración API

**Notas adicionales:**
- La integración debe usar la API oficial de LinkedIn.
- Se debe registrar un log de auditoría para cumplir con el RGPD.

**Estimación:** 16 horas.

## Historia de Usuario 2: Evaluar candidatos con IA

**Título:** Como Reclutador, quiero que el sistema puntúe automáticamente a los candidatos para priorizar a los más prometedores.

**Descripción:** Esta funcionalidad permitirá al reclutador recibir una puntuación automática basada en el análisis de los CVs y los requisitos de la vacante, utilizando el motor de IA del sistema.

**Criterios de Aceptación:**
- Dado que el Reclutador ha recibido aplicaciones para una vacante,
  - Cuando accede a la lista de candidatos,
  - Entonces cada candidato tiene una puntuación visible basada en el análisis del motor de IA.
- Dado que el motor de IA utiliza criterios configurables,
  - Cuando el Reclutador ajusta los criterios de evaluación,
  - Entonces las puntuaciones se recalculan automáticamente.

**Equipo:** Backend, IA

**Notas adicionales:**
- El motor de IA debe ser explicable y cumplir con el RGPD.
- Se debe registrar un log de auditoría para cada cálculo de puntuación.

**Estimación:** 20 horas.

## Historia de Usuario 3: Feedback automatizado para candidatos no seleccionados

**Título:** Como Responsable de RRHH, quiero enviar feedback automatizado a los candidatos no seleccionados para cerrar procesos de manera eficiente y profesional.

**Descripción:** Esta funcionalidad permitirá al Responsable de RRHH generar y enviar automáticamente mensajes personalizados a los candidatos no seleccionados al cerrar una vacante.

**Criterios de Aceptación:**
- Dado que el Responsable de RRHH ha cerrado una vacante,
  - Cuando selecciona la opción de enviar feedback automatizado,
  - Entonces los candidatos no seleccionados reciben un mensaje personalizado.
- Dado que el feedback debe ser claro y profesional,
  - Cuando el sistema genera el mensaje,
  - Entonces incluye detalles básicos como el nombre del candidato y el puesto aplicado.

**Equipo:** Backend, Notificaciones

**Notas adicionales:**
- El sistema debe permitir personalizar plantillas de mensajes.
- Se debe registrar un log de auditoría para cada mensaje enviado, cumpliendo con el RGPD.

**Estimación:** 12 horas.

## Historia de Usuario 4: Interfaz para publicar vacantes en LinkedIn

**Título:** Como Responsable de RRHH, quiero una interfaz intuitiva para publicar vacantes en LinkedIn para facilitar el proceso de publicación.

**Descripción:** Esta funcionalidad permitirá al Responsable de RRHH utilizar una interfaz gráfica para seleccionar y publicar vacantes en LinkedIn, mostrando opciones claras y pasos guiados.

**Criterios de Aceptación:**
- Dado que el Responsable de RRHH accede al sistema,
  - Cuando selecciona una vacante para publicar,
  - Entonces se muestra una interfaz con opciones para configurar y confirmar la publicación en LinkedIn.
- Dado que la publicación requiere autenticación,
  - Cuando el Responsable de RRHH no está autenticado en LinkedIn,
  - Entonces la interfaz muestra un mensaje y un botón para iniciar sesión.

**Equipo:** Frontend, UX/UI

**Notas adicionales:**
- La interfaz debe incluir validaciones visuales para campos obligatorios.
- Debe mostrar un mensaje de éxito o error tras intentar publicar.

**Estimación:** 14 horas.

## Historia de Usuario 5: Interfaz para evaluar candidatos con IA

**Título:** Como Reclutador, quiero una interfaz que muestre las puntuaciones de los candidatos para facilitar la priorización.

**Descripción:** Esta funcionalidad permitirá al Reclutador visualizar las puntuaciones generadas por el motor de IA en una interfaz clara y ordenada, con opciones para ajustar los criterios de evaluación.

**Criterios de Aceptación:**
- Dado que el Reclutador accede a la lista de candidatos,
  - Cuando visualiza la lista,
  - Entonces cada candidato tiene su puntuación claramente visible.
- Dado que los criterios de evaluación son configurables,
  - Cuando el Reclutador ajusta los criterios desde la interfaz,
  - Entonces las puntuaciones se actualizan en tiempo real.

**Equipo:** Frontend, UX/UI

**Notas adicionales:**
- La interfaz debe permitir ordenar y filtrar candidatos por puntuación.
- Debe incluir una explicación breve de cómo se calculan las puntuaciones.

**Estimación:** 18 horas.

## Historia de Usuario 6: Interfaz para enviar feedback automatizado

**Título:** Como Responsable de RRHH, quiero una interfaz para personalizar y enviar feedback automatizado a los candidatos no seleccionados.

**Descripción:** Esta funcionalidad permitirá al Responsable de RRHH utilizar una interfaz gráfica para personalizar plantillas de mensajes y enviar feedback automatizado a los candidatos no seleccionados.

**Criterios de Aceptación:**
- Dado que el Responsable de RRHH ha cerrado una vacante,
  - Cuando accede a la opción de feedback automatizado,
  - Entonces se muestra una interfaz con opciones para personalizar y enviar mensajes.
- Dado que los mensajes deben ser claros y profesionales,
  - Cuando el Responsable de RRHH selecciona una plantilla,
  - Entonces el sistema muestra una vista previa del mensaje.

**Equipo:** Frontend, UX/UI

**Notas adicionales:**
- La interfaz debe incluir un editor de texto para personalizar plantillas.
- Debe mostrar un resumen de los candidatos que recibirán el feedback.

**Estimación:** 16 horas.
