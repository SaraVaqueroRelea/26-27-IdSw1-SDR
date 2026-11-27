# 🎓 Gestión de Actividades Extracurriculares — UNEATLÁNTICO 🎓

> **Ingeniería del Software I · Grupo 5**  
> Plataforma web para administrar el catálogo oficial de actividades extracurriculares, evaluar la participación del alumnado, emitir diplomas acreditativos y gestionar el reconocimiento de créditos ECTS.

---

## 📑 Índice del Proyecto

### 1. Disciplina de Requisitos
* **Información de reuniones**
  * 📄 [Reunión 1](https://github.com/Silviamontes43/26-27-IdSw1-SDR/tree/grupo-5/sesiones/sesion1)
  * 📄 [Reunión 2](https://github.com/Silviamontes43/26-27-IdSw1-SDR/tree/grupo-5/sesiones/sesion2)
  * 📄 [Reunión 3](https://github.com/Silviamontes43/26-27-IdSw1-SDR/tree/grupo-5/sesiones/sesion3)

### 2. Modelo del Dominio
| Artefacto UML | Enlace al repositorio |
| :--- | :--- |
| **Diagrama de Clases** | [Ver `diagramaClases`](https://github.com/Silviamontes43/26-27-IdSw1-SDR/tree/grupo-5/diagramas/diagramaClases) |
| **Diagrama de Objetos** | [Ver `diagramaObjetos`](https://github.com/Silviamontes43/26-27-IdSw1-SDR/tree/grupo-5/diagramas/diagramaObjetos) |
| **Diagrama de Actividades** | [Ver `diagramaActividades`](https://github.com/Silviamontes43/26-27-IdSw1-SDR/tree/grupo-5/diagramas/diagramaActividades) |
| **Diagrama de Estados** | [Ver `diagramaEstados`](https://github.com/Silviamontes43/26-27-IdSw1-SDR/tree/grupo-5/diagramas/diagramaEstados) |
| **Diagrama de Secuencia** | [Ver `diagramaSecuencia`](https://github.com/Silviamontes43/26-27-IdSw1-SDR/tree/grupo-5/diagramas/diagramaSecuencia) |
| **Diagrama de Colaboración** | [Ver `diagramaColaboracion`](https://github.com/Silviamontes43/26-27-IdSw1-SDR/tree/grupo-5/diagramas/diagramaColaboracion) |

### 3. Casos de Uso
* **Actividades de modelado**
  * ✅ [Encontrar actores y casos de uso](https://github.com/Silviamontes43/26-27-IdSw1-SDR/tree/grupo-5/actoresYCasosDeUso)
  * ⏳ Priorizar casos de uso
  * ⏳ Detallar casos de uso
  * ⏳ Prototipar casos de uso
  * ⏳ Estructurar el modelo de casos de uso

---

## 👥 Perfiles y Responsabilidades

| Rol | Responsabilidades en el sistema |
| :--- | :--- |
| **🏛️ Secretario** | • Crea, edita y elimina actividades del catálogo.<br>• Asigna el organizador responsable a cada actividad.<br>• Cierra actas (bloqueando cambios) y realiza correcciones excepcionales.<br>• Consulta historiales y resuelve solicitudes (`ACEPTADA` / `RECHAZADA`). |
| **📋 Organizador** | • Inscribe, edita y da de baja alumnos en actividades abiertas.<br>• Asigna el rol de participación (calcula los créditos automáticamente).<br>• Valida el cumplimiento final como `APTO` o `NO_APTO`.<br>• Exporta listados a Excel y consulta cursos anteriores en modo solo lectura. |
| **🎓 Alumno** | • Consulta su historial extracurricular y el desglose de créditos.<br>• Descarga diplomas de actividades superadas (`APTO`).<br>• Presenta solicitudes de acreditación o convalidación de optativa. |

---

## ⚙️ Reglas de Negocio Clave

### 🏅 Evaluación y Diplomas
* **Sin control de asistencia:** La evaluación depende únicamente de cumplir los requisitos del rol asignado (`EN_CURSO` → `APTO` o `NO_APTO`).
* **Créditos asociados al rol:** Cada actividad define sus propios roles (ej. *Participante*, *Capitán*, *Orador*) con su carga en ECTS y criterios específicos.
* **Descarga condicionada:** Solo se genera código de diploma y se habilita su descarga cuando la participación es `APTO`.

### 📊 Cálculo del Historial y Topes
* **Límite por categoría:** Cada categoría normativa fija un máximo de créditos validables; el excedente acumulado en una misma categoría no computa para convalidación.
* **Saldo dinámico:** El historial calcula en tiempo real los créditos **acumulados**, **validables** (aplicando topes), **canjeados** y **disponibles**.

### 📩 Tramitación de Solicitudes

| Tipo de Solicitud | Requisito mínimo | Efecto al aprobarse |
| :--- | :--- | :--- |
| **Acreditación de Historial** | Tener más de **0 ECTS** acumulados. | Emite certificado oficial sin descontar créditos del saldo. |
| **Convalidación de Optativa** | Disponer de al menos **6.0 ECTS validables**. | Canjea y descuenta **6.0 ECTS** del saldo disponible. |

### 🔒 Control de Edición
* Cuando **Secretaría cierra una actividad**, el organizador pasa automáticamente a modo **solo lectura**; únicamente Secretaría puede efectuar modificaciones excepcionales.
