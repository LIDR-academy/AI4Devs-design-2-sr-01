# Prompts utilizados en el ejercicio (ChatGPT 4.1)

## Prompt inicial

Para el prompt inicial, utilicé el siguiente:

```
Eres un product manager experto en business analysis y redacción de historias de usuario y casos de uso, así como en la creación de tickets de trabajo completos, incluyendo su estimación de desempeño y priorización en tiempos de entrega.  

Te voy a proporcionar un archivo .md que conforma un Documento de Requisitos del Producto (PRD) sobre una plataforma de gestión de talento y personal llamada LTI. Teniendo en cuenta las 3 funcionalidades principales que se explican en él, quiero que primero generes las User Stories de cada una de las 3 funcionalidades (de una en una, empezaremos por la primera) utilizando la siguiente estructura:  
"Como [rol de usuario], quiero [objetivo] para que pueda [beneficio]" 

Luego, para cada user story te voy a pedir que generes el caso de uso asociado a esa user story. La estructura que debes usar para redactar un caso de uso es la siguiente:

1.Descripción General
Propósito: ¿Qué problema resuelve este caso de uso?
 (e.g., "Permitir a un nuevo usuario crear una cuenta en la aplicación para acceder a sus funcionalidades").
Alcance: Área funcional o módulo al que pertenece (e.g., "Módulo de autenticación").
Actores principales: ¿Quién interactúa con el sistema?
 (e.g., "Usuario final", "API de backend").
Precondiciones: Estados o configuraciones necesarias para que se pueda iniciar el flujo.
 (e.g., "El usuario no debe estar autenticado").
Postcondiciones: Estados finales esperados tras la ejecución exitosa.
 (e.g., "Se crea una cuenta y el usuario recibe un mensaje de confirmación").
2. Flujo Principal (Camino Feliz)
Enumera paso a paso las acciones esperadas en un escenario exitoso:
3. Flujos Alternativos
Incluye variaciones al flujo principal, como decisiones opcionales o bifurcaciones:
4. Flujos de Excepción (Errores)
Detalla escenarios donde se interrumpe el flujo esperado debido a errores:
5. Requisitos Técnicos
Requisitos funcionales:
6. Criterios de Validación (Pruebas del Desarrollo)
Define cómo se verificará que el caso de uso está implementado correctamente:
Pruebas técnicas:
Pruebas de integración:
7. Definition of done

Tanto las user story como los casos de uso, quiero que me los escribas en formato Markdown para poder añadirlo a mi documentación del proyecto.

Antes de empezar con el proceso, tienes alguna duda?
```

Con esto, ChatGPT me preguntó una serie de dudas:

```
¿Quieres que la redacción sea formal y orientada a documentación, o prefieres un tono más conversacional?

¿Deseas que identifique explícitamente el nombre o número de la funcionalidad principal según el PRD, o basta con que nombre cada historia/caso de uso según el objetivo funcional?

¿Debo incluir ejemplos de datos ficticios (como nombres de usuario, empresa, roles, etc.) en los flujos, o mantenerlo genérico?

¿Hay algún sistema de priorización o estimación que prefieres (ejemplo: MoSCoW, Story Points, T-shirt size, etc.) para añadir a los tickets después?
```

Tras responder a estas preguntas, continué con el proceso de generación de las User Stories y los casos de uso sin mayor complicación

## Generaciín tickets de trabajo

Tras tener las User Stories y los casos de uso, utilicé el siguiente prompt para generar los tickets de trabajo, adjuntando el archivo .md generado hasta el momento:

```
Aquí tengo las 3 user stories con sus casos de uso. 
Ahora quiero generar un backlog de tickets de trabajo teniendo en cuenta maquetación del frontend, desarollo del backend (cuando sea necesario) e integración de ambos. 
Agrupalos por epicas de trabajo de los 3 casos de uso
```

Obteniendo los resultados que se muestran en el archivo `UserStories-RPS.md`.


## Generación de sprints priorizados

Para generar los sprints priorizados, utilicé el siguiente prompt:

```
Siguiendo una metodología ágil, podrías dividir los tickets en sprints de trabajo, teniendo en cuenta sprints de 2 semanas con 2 desarrolladores trabajando simultaneamente (uno con el frontend y otro con el backend). 
Intenta que siempre que se tenga que realizar un ticket de integración, la parte del backend de esa epica esté ya realizada
```

## Conclusiones finales

El proceso de generación de User Stories, casos de uso y tickets de trabajo fue fluido y eficiente. Utilizando prompts claros y estructurados, pude obtener resultados que se alinean con las necesidades del proyecto LTI.
La interacción con ChatGPT fue productiva, y las respuestas fueron coherentes y útiles para la documentación y planificación del proyecto.
