# Título de la Historia de Usuario: Crear oferta de empleo

**Como** usuario del departamento de RRHH,  
**quiero** crear una nueva oferta de empleo en el sistema ATS,  
**para que** poder iniciar un proceso de selección de personal.

---

## Criterios de Aceptación

- El sistema debe permitir introducir el título, descripción, requisitos y localización de la oferta  
- La oferta debe poder guardarse como borrador o publicarse directamente  
- Debe asignarse un identificador único a cada nueva oferta  

---

## Notas Adicionales

- Se recomienda permitir duplicar ofertas anteriores para facilitar la creación  
- El creador de la oferta deberá tener permisos de RRHH  

---

## Historias de Usuario Relacionadas

- Publicar oferta en portales  
- Aplicar a oferta  


---

# Título de la Historia de Usuario: Publicar oferta en portales

**Como** usuario del departamento de RRHH,  
**quiero** publicar las ofertas creadas en portales externos de empleo,  
**para que** aumentar la visibilidad y recibir más candidaturas.

---

## Criterios de Aceptación

- El sistema debe permitir seleccionar a qué portales se publica (InfoJobs, LinkedIn, etc.)  
- Debe registrar el estado de publicación y la fecha en cada portal  
- El sistema debe gestionar errores de integración y mostrar mensajes claros  

---

## Notas Adicionales

- Es posible que algunos portales requieran configuraciones específicas  
- Debe incluirse una funcionalidad para cancelar la publicación  

---

## Historias de Usuario Relacionadas

- Crear oferta de empleo  


---

# Título de la Historia de Usuario: Cribar y puntuar candidatos

**Como** usuario del departamento de RRHH,  
**quiero** cribar y puntuar a los candidatos que han aplicado a una oferta,  
**para que** identificar los perfiles más adecuados para avanzar en el proceso.

---

## Criterios de Aceptación

- El sistema debe mostrar el listado de candidatos con su CV y carta de presentación  
- El usuario podrá puntuar con un sistema estandarizado (por ejemplo, 1 a 5 estrellas)  
- Debe registrarse la puntuación y comentarios del evaluador  

---

## Notas Adicionales

- El sistema debería permitir filtrar candidatos por puntuación y estado  
- La puntuación no debe ser visible para el candidato  

---

## Historias de Usuario Relacionadas

- Aplicar a oferta  
- Programar entrevistas  


---

# Título de la Historia de Usuario: Programar entrevistas

**Como** usuario del departamento de RRHH,  
**quiero** programar entrevistas con los candidatos seleccionados,  
**para que** coordinar el proceso de entrevistas de forma organizada.

---

## Criterios de Aceptación

- Debe poder asignarse una fecha y hora a cada entrevista  
- El sistema debe notificar al candidato y al entrevistador  
- Debe registrarse el estado de la entrevista (pendiente, realizada, cancelada)  

---

## Notas Adicionales

- Idealmente se integrará con Google Calendar o Outlook  
- Debe permitir reprogramar o cancelar entrevistas  

---

## Historias de Usuario Relacionadas

- Evaluar entrevistas  
- Recibir notificaciones y citas  


---

# Título de la Historia de Usuario: Evaluar entrevistas

**Como** usuario del departamento de RRHH,  
**quiero** registrar la evaluación de una entrevista realizada,  
**para que** valorar de forma estructurada el rendimiento del candidato en la entrevista.

---

## Criterios de Aceptación

- Debe poder introducirse una puntuación global y comentarios  
- Las evaluaciones deben ser visibles solo para los responsables de RRHH  
- Debe poder consultarse el historial de evaluaciones por candidato  

---

## Notas Adicionales

- Se recomienda incluir criterios objetivos en la evaluación  
- Podría generarse un informe automático por cada entrevista  

---

## Historias de Usuario Relacionadas

- Programar entrevistas  
- Cribar y puntuar candidatos  


---

# Título de la Historia de Usuario: Aplicar a oferta

**Como** candidato externo,  
**quiero** aplicar a una oferta de empleo publicada,  
**para que** poder optar a un puesto de trabajo.

---

## Criterios de Aceptación

- Debe poder subirse un CV y completar un formulario  
- El sistema debe confirmar que la solicitud se ha enviado correctamente  
- La oferta debe cerrarse automáticamente al alcanzar un número máximo de aplicaciones (si se ha definido)  

---

## Notas Adicionales

- Debe ser posible aplicar con cuenta de LinkedIn  
- El sistema debe validar campos obligatorios del formulario  

---

## Historias de Usuario Relacionadas

- Crear oferta de empleo  
- Cribar y puntuar candidatos  


---

# Título de la Historia de Usuario: Recibir notificaciones y citas

**Como** candidato externo,  
**quiero** recibir notificaciones del estado de su candidatura y citas de entrevista,  
**para que** mantenerse informado sobre el proceso de selección.

---

## Criterios de Aceptación

- Debe recibir notificaciones por correo o SMS si se configura  
- Debe poder visualizar el calendario de entrevistas  
- Debe recibir confirmaciones automáticas al cambiar su estado en el proceso  

---

## Notas Adicionales

- Se recomienda permitir al candidato elegir el canal de notificación preferido  
- Las notificaciones deben ser multilingües si es necesario  

---

## Historias de Usuario Relacionadas

- Programar entrevistas  


---

