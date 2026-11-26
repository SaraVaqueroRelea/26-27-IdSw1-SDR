# Diagrama de Casos de Uso
## Sistema de Actividades Extracurriculares – UNEATLÁNTICO

### 1. Introducción

El sistema de Actividades Extracurriculares de UNEATLÁNTICO permite gestionar las actividades organizadas por la universidad, controlar la participación de los alumnos, registrar sus asistencias y tramitar solicitudes relacionadas con el reconocimiento de créditos y la acreditación de su historial.

En el sistema intervienen tres actores principales:

- **Organizador:** responsable de gestionar las actividades y controlar la participación y asistencia de los alumnos.
- **Alumno:** puede consultar su historial de participaciones y realizar solicitudes.
- **Secretario:** encargado de administrar las actividades y resolver las solicitudes presentadas por los alumnos.

---

### 2. Casos de uso del Organizador

El organizador es el encargado de gestionar las actividades extracurriculares y supervisar la participación de los alumnos.

Sus principales casos de uso son:

**2.1. Añadir participante a una actividad**

Permite incorporar un alumno a una actividad extracurricular. Para ello, el organizador debe:

- Seleccionar al alumno que desea incorporar.
- Asignarle un rol de participación dentro de la actividad.

**2.2. Registrar asistencia**

Permite registrar la asistencia de los participantes a una actividad. Para realizar esta operación es necesario:

- Indicar la fecha de asistencia.
- Establecer el estado de asistencia, que puede ser:
  - Presente.
  - Falta justificada.
  - Falta injustificada.

**2.3. Cerrar actividad**

Permite al organizador cerrar una actividad cuando haya finalizado, evitando que continúe su gestión como actividad abierta.

---

### 3. Casos de uso del Alumno

El alumno puede consultar la información relacionada con sus participaciones en actividades extracurriculares y realizar solicitudes a la universidad.

Sus principales casos de uso son:

**3.1. Consultar historial de participaciones**

Permite al alumno consultar las actividades en las que ha participado, así como la información relacionada con sus participaciones.

**3.2. Crear solicitud**

Permite al alumno presentar una solicitud relacionada con sus actividades extracurriculares.

Para crearla debe:

- Seleccionar el tipo de solicitud.
- Indicar los créditos que desea solicitar, cuando corresponda.

Existen dos tipos de solicitudes:

- **Convalidación optativa:** solicitud para reconocer créditos como asignaturas optativas.
- **Acreditación del historial:** solicitud para acreditar oficialmente la participación del alumno en actividades extracurriculares.

---

### 4. Casos de uso del Secretario

El secretario es el responsable de administrar las actividades extracurriculares y gestionar las solicitudes presentadas por los alumnos.

Sus principales casos de uso son:

**4.1. Crear actividad**

Permite registrar una nueva actividad extracurricular en el sistema. Durante su creación se debe asignar un organizador responsable de gestionarla.

**4.2. Eliminar actividad**

Permite eliminar una actividad que ya no deba formar parte del sistema.

**4.3. Resolver solicitud**

Permite al secretario revisar y resolver las solicitudes presentadas por los alumnos.

Existen dos posibles resultados:

- **Aceptar solicitud:** la solicitud queda aceptada.
- **Rechazar solicitud:** la solicitud queda rechazada y se puede indicar el motivo del rechazo.

Los estados posibles de una solicitud son:

- Pendiente.
- Aceptada.
- Rechazada.

---

### 5. Relaciones entre los casos de uso

En el diagrama UML se utilizan tres tipos de relaciones:

**5.1. Relación `<<include>>`**

Indica que un caso de uso necesita ejecutar obligatoriamente otro para completar su funcionamiento.

Se utiliza en los siguientes casos:

- Añadir participante incluye seleccionar alumno y asignar rol de participación.
- Registrar asistencia incluye indicar fecha e indicar estado de asistencia.
- Crear solicitud incluye seleccionar tipo de solicitud y solicitar créditos.
- Crear actividad incluye asignar organizador.

**5.2. Relación `<<extend>>`**

Representa un comportamiento opcional que amplía otro caso de uso.

Se utiliza en el siguiente caso:

- Indicar motivo del rechazo amplía el caso de uso rechazar solicitud, ya que el secretario puede especificar por qué se rechaza.

**5.3. Generalización**

Representa diferentes formas de realizar un mismo caso de uso.

En este sistema:

- Aceptar solicitud y rechazar solicitud son dos especializaciones de resolver solicitud.

---

### 6. Resumen general de los actores

| Actor | Funcionalidades principales |
|---|---|
| Organizador | Añadir participantes, asignar roles, registrar asistencias y cerrar actividades. |
| Alumno | Consultar historial de participaciones y crear solicitudes. |
| Secretario | Crear y eliminar actividades, asignar organizadores y resolver solicitudes. |

### 7. Conclusión

El diagrama de casos de uso representa las principales funcionalidades del sistema de Actividades Extracurriculares de UNEATLÁNTICO desde el punto de vista de sus tres actores.

Cada actor dispone de unas responsabilidades concretas que permiten gestionar las actividades, controlar la participación de los alumnos y tramitar las solicitudes de manera organizada.

Este diagrama complementa el diagrama de clases, ya que muestra las operaciones que puede realizar cada actor y cómo interactúa con el sistema.
