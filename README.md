# Sistema de Gestión de Actividades Extracurriculares — UNEATLÁNTICO

Plataforma web para administrar el catálogo de actividades extracurriculares, evaluar la participación del alumnado, emitir diplomas y gestionar el reconocimiento académico de créditos ECTS.

---

## Perfiles y Responsabilidades

| Rol | Funciones principales |
| :--- | :--- |
| **Secretario** | • Crea, edita y elimina actividades.<br>• Asigna el organizador responsable a cada actividad.<br>• Cierra actas (bloqueando edición) y realiza correcciones excepcionales.<br>• Consulta historiales y resuelve solicitudes (`ACEPTADA` / `RECHAZADA`). |
| **Organizador** | • Inscribe, edita y da de baja alumnos en actividades abiertas.<br>• Asigna el rol de participación (calcula los créditos automáticamente).<br>• Evalúa el cumplimiento final como `APTO` o `NO_APTO`.<br>• Exporta listados a Excel y consulta cursos anteriores en modo solo lectura. |
| **Alumno** | • Consulta su historial extracurricular y el desglose de créditos.<br>• Descarga diplomas de actividades superadas (`APTO`).<br>• Presenta solicitudes de acreditación o convalidación de optativa. |

---

## Reglas de Negocio Clave

### 1. Evaluación y Créditos
* **Sin control de asistencia:** La evaluación se basa exclusivamente en cumplir los requisitos del rol asignado (`EN_CURSO` $\rightarrow$ `APTO` o `NO_APTO`).
* **Créditos por rol:** Cada actividad define sus propios roles (ej. *Participante*, *Capitán*, *Orador*) con una carga de ECTS y requisitos específicos.
* **Emisión de diplomas:** Solo se genera código de diploma y se habilita su descarga cuando la participación es `APTO`.

### 2. Cálculo del Historial y Topes
* **Límite por categoría:** Cada categoría normativa establece un máximo de créditos validables; si un alumno supera ese tope en una misma categoría, el excedente no computa para convalidación.
* **Cálculo dinámico:** El historial muestra en tiempo real los créditos **acumulados**, **validables** (tras aplicar topes), **canjeados** y **disponibles**.

### 3. Solicitudes del Alumno

| Tipo de Solicitud | Requisito mínimo | Efecto al aprobarse |
| :--- | :--- | :--- |
| **Acreditación de Historial** | Tener más de **0 ECTS** acumulados. | Emite certificado oficial sin descontar créditos del saldo. |
| **Convalidación de Optativa** | Disponer de al menos **6.0 ECTS validables**. | Canjea y descuenta **6.0 ECTS** del saldo disponible. |

### 4. Control de Edición
* Una vez que **Secretaría cierra una actividad**, el organizador pasa a modo **solo lectura**; únicamente Secretaría puede modificar datos de forma excepcional.
