# Resumen de la sesión 3

## 1. Objetivo de la reunión

La tercera sesión sirvió para concretar el funcionamiento detallado de la plataforma, cerrar decisiones de alcance que habían quedado abiertas en reuniones anteriores y definir con precisión los permisos de cada tipo de usuario.

El objetivo principal fue pasar de una visión general de la herramienta a unas reglas de negocio claras que permitan simplificar el panel de gestión y comenzar directamente con el modelado del dominio del sistema.

## 2. Simplificación del panel y enfoque de la plataforma

Durante la sesión se acordó simplificar el panel de gestión para evitar pantallas sobrecargadas y centrar la aplicación en las tareas reales del día a día universitario.

La plataforma actuará como un sistema único dedicado al registro, seguimiento y acreditación de las actividades extracurriculares propias de la Universidad Europea del Atlántico (UNEATLÁNTICO), eliminando flujos que no aporten valor directo al control de participación ni a la gestión de créditos.

## 3. Usuarios, roles y permisos definitivos

Se establecieron tres perfiles de usuario bien diferenciados y excluyentes entre sí, asociados cada uno a una persona dentro del sistema (por lo que un alumno no puede desempeñar funciones de organizador):

* **Secretario / Administrador:** tiene control global del catálogo y de las validaciones oficiales. Puede crear o eliminar actividades, asignar al organizador responsable de cada una, consultar los historiales y revisar las solicitudes enviadas por los alumnos para aceptarlas o rechazarlas.
* **Organizador de la actividad:** figura encargada de dirigir una actividad concreta. Cada actividad contará con un **único organizador** asignado. Sus funciones son añadir a los alumnos participantes, asignarles su rol dentro de la actividad, controlar la asistencia, gestionar las justificaciones de faltas y cerrar la actividad al finalizar.
* **Alumno:** usuario final de consulta y tramitación. Puede revisar en cualquier momento su historial de actividades extracurriculares, comprobar su saldo de créditos y presentar solicitudes a través de la web.

## 4. Gestión de actividades, asistencia y cierre

Se definió con mayor detalle el ciclo de vida de cada actividad gestionada por su organizador:

* **Registro de participantes y roles:** el organizador incorpora a los alumnos y les asigna el rol correspondiente dentro de la actividad, al que van ligados los requisitos mínimos y los créditos a conceder.
* **Control de asistencia mediante colores:** para agilizar el seguimiento en el panel, la asistencia de cada alumno se representará visualmente mediante un código de colores (presente, falta justificada y falta injustificada), facilitando además el registro y la revisión de justificantes de falta.
* **Estado del alumno y cierre de la actividad:** cada participación registrará el estado del estudiante (en curso, superada o no superada). Una vez concluida la actividad, el organizador procederá a su cierre oficial.
* **Consulta histórica en modo solo lectura:** tras el cierre, los organizadores podrán seguir consultando el historial de actividades anteriores, pero sin posibilidad de modificar los datos ya cerrados.

## 5. Automatización de créditos, diplomas y saldo global

Se concretó cómo se calculan, conceden y acumulan los créditos sin cargar de trabajo manual innecesario a los departamentos:

* **Asignación automática por cumplimiento:** cuando un estudiante cumple los requisitos mínimos definidos para su rol (asistencia y dedicación), el sistema le concede automáticamente los créditos correspondientes a esa actividad y habilita la acreditación de haberla superado.
* **Generación de diplomas:** la plataforma incorporará la emisión de diplomas acreditativos de las actividades completadas satisfactoriamente.
* **Saldo global de créditos:** todos los créditos obtenidos en las distintas actividades superadas pasan a formar parte de un saldo global del alumno, sobre el que se controla tanto el total acumulado como los créditos disponibles para canje.

## 6. Historial extracurricular y tipos de solicitud del alumno

El alumno dispondrá de su historial extracurricular organizado por **ámbito** y por **curso académico**, pudiendo decidir el destino de los créditos obtenidos mediante una solicitud realizada directamente desde la web:

* **Convalidación de una asignatura optativa:** el estudiante podrá solicitar el reconocimiento de créditos para convalidar una optativa siempre que cuente, como mínimo, con los créditos requeridos por dicha asignatura (tomando como referencia los 6 créditos). Una vez que Secretaría revisa los datos y aprueba la solicitud, los créditos utilizados se restan del saldo disponible y el reconocimiento queda reflejado en su expediente académico.
* **Acreditación de mérito extracurricular (salida de la universidad):** el estudiante podrá solicitar un certificado oficial de su historial de actividades extracurriculares con los créditos que tenga acumulados, sin exigir un mínimo concreto, para acreditar su participación en la vida universitaria al finalizar sus estudios.

En ambos casos, el trámite se inicia en la plataforma web y corresponde a Secretaría verificar la información de la solicitud para aprobarla o denegarla definitivamente.

## 7. Decisión sobre actividades externas

A diferencia de lo planteado inicialmente en la segunda sesión, se determinó que las **actividades externas** (como titulaciones de música, danza o seminarios realizados fuera de la universidad) **quedan fuera del alcance de la plataforma web**.

Cuando un estudiante desee convalidar este tipo de actividades, deberá acudir presencialmente a Secretaría y aportar allí la acreditación correspondiente. De este modo, la aplicación se enfoca exclusivamente en el historial de actividades organizadas por la propia universidad.

## 8. Ámbitos y tipología de actividades de UNEATLÁNTICO

Las actividades gestionadas en el sistema se clasificarán en los grandes ámbitos de vida universitaria que ofrece UNEATLÁNTICO (presentados cada curso en la Feria Vive tu Campus):

* **Deportes y actividad física:** grupos y entrenamientos regulares (voleibol, baloncesto, fútbol sala), torneos universitarios internos (voleibol, baloncesto 3×3, bádminton, pickleball, tenis de mesa) y talleres de iniciación («Descubre + Deporte»).
* **Clubes, debate y participación estudiantil:** Liga de Debate (incluyendo formación en oratoria y argumentación), Club de Lectura y grupos o comunidades estudiantiles (Espacio Joven, voluntariado, GeekAtlantico).
* **Cultura e idiomas:** Aula de Teatro, cinefórums, exposiciones, seminarios y propuestas de intercambio cultural vinculadas al área de Español Lengua Extranjera (ELE).

## 9. Orientaciones para el modelado y diseño del sistema

A partir de los acuerdos de esta sesión, se establecieron criterios claros para abordar la Disciplina de Requisitos y el diseño inicial:

* Mantener un modelo de clases claro y sencillo, evitando estructuras excesivamente complejas que no respondan a una necesidad directa del cliente.
* Reflejar fielmente las restricciones de negocio acordadas: organizador único por actividad, separación estricta entre los tres perfiles de usuario, cierre inmutable de actividades y gestión de saldo global.
* Separar con claridad las responsabilidades entre la automatización interna (cálculo de cumplimiento, créditos y diplomas) y la validación oficial de Secretaría (resolución de solicitudes).

## 10. Próximos pasos y organización

Con el alcance funcional y las reglas principales cerradas, el equipo acordó:

* Elaborar y refinar el **Modelo del Dominio** mediante el diagrama de clases en formato PlantUML (`.puml`), incorporando atributos, tipos, visibilidades, relaciones y operaciones principales.
* Validar el diagrama con los requisitos de las tres sesiones y con los bocetos visuales de las vistas de alumno y organizador.
* Preparar la documentación de requisitos para avanzar a las siguientes fases del proyecto.

## Conclusiones principales de la sesión

Las cinco ideas clave que se cierran tras esta reunión son:

1. El panel de gestión se simplifica en torno a tres perfiles excluyentes (Secretario, Organizador único por actividad y Alumno).
2. El seguimiento incorpora control de asistencia por colores, justificación de faltas, cierre de actividades y consulta histórica de solo lectura para organizadores.
3. El cumplimiento de requisitos automatiza la concesión de créditos y la generación de diplomas, alimentando un saldo global del estudiante.
4. El alumno tramita desde la web su solicitud para convalidar una optativa (exigiendo el mínimo de créditos de la asignatura y restándolos al aprobarse) o para acreditar su historial extracurricular, quedando siempre sujeta a la validación final de Secretaría.
5. Las actividades externas se gestionan presencialmente en Secretaría y quedan fuera de la web, centrando la herramienta en el historial de actividades propias de UNEATLÁNTICO.

En definitiva, esta sesión permitió aterrizar las necesidades de la universidad en reglas concretas y operativas, dejando acotado el alcance real de la plataforma y sentando una base sólida para construir el modelo del dominio sin ambigüedades.
