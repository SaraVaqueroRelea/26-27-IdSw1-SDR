# Actores y Casos de Uso — Gestión de Actividades Extracurriculares (UNEATLÁNTICO)

Este documento define los actores y casos de uso del sistema siguiendo la metodología **RUP**, alineados con las reglas de negocio del **Modelo del Dominio (v5.10)**.

## Catálogo de Actores

### Actor Abstracto: `Usuario`

Representa a cualquier miembro autenticado de la comunidad universitaria (identificado por `dni`, `nombre`, `apellidos` y `correoInstitucional`). De este actor heredan `Secretario`, `Organizador` y `Alumno`.

| Caso de Uso | Descripción | 
| ----- | ----- | 
| **Iniciar sesión** | Autentica al usuario en el sistema y carga la vista correspondiente a su rol (`Secretario`, `Organizador` o `Alumno`). | 
| **Cerrar sesión** | Finaliza la sesión activa del usuario de forma segura. | 

### Actor: `Secretario` *(hereda de `Usuario`)*

Personal administrativo encargado de administrar el catálogo oficial de actividades, asignar responsables, cerrar actas y resolver las solicitudes de reconocimiento de créditos.

| Caso de Uso | Descripción y Reglas de Negocio | 
| ----- | ----- | 
| **Crear actividad** | Da de alta una actividad indicando nombre, descripción, departamento, curso académico, `Categoria` (normativa y tope máximo) y sus `RolParticipacion` con sus créditos y requisitos. | 
| **Editar o eliminar actividad** | Modifica los datos de una actividad abierta o la elimina si aún no tiene participaciones consolidadas. | 
| **Asignar organizador** | Vincula un único `Organizador` responsable a una actividad. | 
| **Cerrar actividad** | Marca la actividad como `cerrada = true`, bloqueando cualquier modificación por parte del organizador. | 
| **Modificar actividad cerrada** | Permite a Secretaría realizar correcciones excepcionales sobre una actividad ya cerrada (reapertura o edición administrativa). | 
| **Consultar actividades y expedientes** | Visualiza cualquier actividad del catálogo y consulta el `HistorialExtracurricular` de cualquier alumno. | 
| **Resolver solicitud** | Evalúa una `Solicitud` en estado `PENDIENTE` y la marca como `ACEPTADA` o `RECHAZADA` (indicando motivo). Si es convalidación de optativa y se acepta, descuenta 6.0 ECTS del saldo disponible del alumno. | 

### Actor: `Organizador` *(hereda de `Usuario`)*

Responsable de coordinar los participantes de las actividades que tiene asignadas durante el curso vigente y evaluar el cumplimiento de los requisitos.

| Caso de Uso | Descripción y Reglas de Negocio | 
| ----- | ----- | 
| **Añadir miembro a actividad** | Inscribe a un `Alumno` (por `dni` o `numeroCarnet`) en una actividad abierta, creando su `Participacion` en estado inicial `EN_CURSO` e incluyendo la asignación de su rol. | 
| **Editar o eliminar miembro** | Modifica los datos de inscripción de un participante o lo da de baja mientras la actividad siga abierta. | 
| **Asignar rol de participación** | Asigna o cambia el `RolParticipacion` del miembro; el sistema calcula automáticamente los `creditosAsignados` según el rol seleccionado. | 
| **Validar requisitos de participación** | Evalúa si el alumno ha cumplido los requisitos del rol al finalizar la actividad y establece su estado en `APTO` o `NO_APTO`. | 
| **Exportar miembros a Excel** | Genera un archivo descargable con el listado de participantes, roles, créditos y estados de la actividad. | 
| **Consultar actividades de otros cursos** | Permite visualizar en modo **solo lectura** las actividades y listados de cursos académicos anteriores. | 

### Actor: `Alumno` *(hereda de `Usuario`)*

Estudiante que consulta su trayectoria extracurricular, descarga sus diplomas acreditativos y tramita de forma opcional el reconocimiento de créditos.

| Caso de Uso | Descripción y Precondiciones | 
| ----- | ----- | 
| **Consultar historial extracurricular** | Muestra todas sus participaciones (filtrables por curso o categoría), los diplomas obtenidos y el desglose de créditos (acumulados, validables por categoría aplicando topes máximos, canjeados y disponibles). | 
| **Descargar diploma** | Genera y descarga el certificado acreditativo de una actividad. **Precondición:** la `Participacion` debe estar en estado `APTO`. | 
| **Solicitar acreditación de historial** | Crea una solicitud oficial (`ACREDITACION_HISTORIAL`) para certificar sus méritos en el expediente sin consumir créditos. **Precondición:** tener créditos acumulados (`> 0 ECTS`). | 
| **Solicitar convalidación de optativa** | Crea una solicitud (`CONVALIDACION_OPTATIVA`) para canjear créditos por una asignatura optativa. **Precondición:** disponer de al menos **6.0 ECTS validables** tras aplicar el límite máximo de cada `Categoria`. | 