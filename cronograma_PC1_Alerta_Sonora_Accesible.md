# Cronograma de Construcción
## Proyecto Integrador de IA para Negocios — AD5018
### MVP: Alerta Sonora Accesible

**Equipo:** Harold Inca · Diego Requena · Jennifer Patiño  
**Semana actual:** 5  
**PC1:** Semana 6  
**Periodo principal de construcción:** Semanas 7–13  
**PC2:** Semana 14  
**Fin del ciclo académico:** Semana 18

---

## 1. Objetivo del cronograma

Organizar la construcción, integración, validación y documentación del MVP **Alerta Sonora Accesible** después de la PC1, asignando responsables claros por semana y manteniendo el alcance comprometido:

- componente analítico **A3**;
- componente generativo **G1**;
- patrón **Modelo → Lenguaje**;
- despliegue mediante URL pública;
- validación con usuarios y evidencia real.

---

## 2. Roles propuestos

Para distribuir el trabajo de forma equilibrada:

### Harold Inca — Modelo y datos
Responsable principal de:
- organización del dataset;
- entrenamiento en Teachable Machine;
- evaluación de métricas;
- matriz de confusión;
- identificación de errores;
- recolección adicional;
- reentrenamiento V2.

### Diego Requena — Desarrollo e integración
Responsable principal de:
- interfaz web;
- captura de audio;
- integración con el modelo;
- conexión con G1;
- despliegue;
- pruebas técnicas.

### Jennifer Patiño — Producto, validación y documentación
Responsable principal de:
- prompt G1;
- reglas de criticidad y umbrales;
- diseño de pruebas con usuarios;
- registro de resultados;
- documentación;
- riesgos y preparación de sustentación.

> **Responsabilidad compartida:** aunque exista un responsable principal por tarea, los tres integrantes deben conocer y poder explicar cualquier fase del proyecto.

---

## 3. Cronograma general

| Semana | Fase | Actividades principales | Responsable principal | Apoyo | Entregable / evidencia |
|---|---|---|---|---|---|
| **5** | P + R + O | Cerrar Plantillas 1, 2 y 3; README; resumen ejecutivo; cronograma; revisar coherencia de métricas, datos y alcance | Jennifer | Harold y Diego | Documentación PC1 completa |
| **6** | PC1 | Preparar deck, ensayar sustentación, revisar repositorio y entregar PC1 | Equipo completo | — | `presentacion_pc1.pdf` + repositorio |
| **7** | M1 | Completar dataset, verificar licencias, ordenar clases y confirmar volumen real por categoría | Harold | Jennifer | Dataset organizado + registro de fuentes |
| **8** | M1 / M2 | Entrenar modelo V1, exportar modelo y registrar métricas iniciales | Harold | Diego | Modelo V1 + primeras métricas |
| **9** | M2 | Construir interfaz web mínima, habilitar micrófono e integrar inferencia del modelo | Diego | Harold | Prototipo funcional local |
| **10** | M2 | Integrar G1, reglas de criticidad y umbrales; realizar pruebas extremo a extremo | Diego y Jennifer | Harold | Flujo Modelo → Lenguaje funcional |
| **11** | M2 | Desplegar MVP por URL pública y probarlo desde dispositivos externos | Diego | Equipo completo | MVP público V1 |
| **12** | P2 | Validar con 5 usuarios / 50 observaciones; registrar errores, tiempos y comprensión | Jennifer | Harold y Diego | `pruebas_usuario.md` |
| **13** | P2 + T | Analizar resultados, recolectar nuevos audios, reentrenar V2, comparar métricas, documentar riesgos y resultados | Harold y Jennifer | Diego | V2 + `resultados_okr.md` + Plantilla 4 |
| **14** | PC2 | Demo en vivo, resultados, riesgos, ética y lecciones aprendidas | Equipo completo | — | `presentacion_pc2.pdf` + MVP final |

---

## 4. Detalle por semana

### Semana 5 — Cierre de propuesta

**Objetivo:** dejar lista la estructura completa de la PC1.

**Actividades:**
- revisar Problem Statement;
- revisar Data Readiness;
- cerrar AI Product Canvas;
- confirmar A3 + G1;
- cerrar README;
- cerrar resumen ejecutivo;
- cerrar cronograma;
- verificar que no haya contradicciones entre documentos.

**Responsable principal:** Jennifer  
**Apoyo:** Harold y Diego

**Criterio de cierre:** todos los archivos de PC1 existen y cuentan la misma historia.

---

### Semana 6 — Entrega y sustentación PC1

**Objetivo:** defender la propuesta completa.

**Actividades:**
- preparar presentación;
- verificar repositorio GitHub;
- practicar preguntas;
- revisar problema, datos, stack, métricas y alcance;
- confirmar que todos puedan responder sobre cualquier fase.

**Responsable:** equipo completo.

**Criterio de cierre:** PC1 entregada y sustentada.

---

### Semana 7 — Dataset final

**Objetivo:** transformar el inventario previsto en un dataset real y trazable.

**Actividades:**
- completar audios por clase;
- registrar número real de muestras;
- revisar calidad;
- eliminar clips problemáticos;
- registrar fuente y licencia;
- mantener balance entre clases.

**Responsable principal:** Harold

**Meta inicial:**
- alarma: 50;
- detector de humo: 50;
- timbre: 50;
- bocina: 50;
- ruido de fondo: 60.

**Criterio de cierre:** dataset organizado y disponible para entrenamiento.

---

### Semana 8 — Modelo V1

**Objetivo:** entrenar y evaluar la primera versión del clasificador.

**Actividades:**
- entrenar en Teachable Machine;
- separar entrenamiento y evaluación según el flujo elegido;
- calcular accuracy;
- calcular precision y recall por clase;
- revisar matriz de confusión;
- identificar falsos negativos;
- exportar modelo.

**Responsable principal:** Harold  
**Apoyo:** Diego

**Criterio de cierre:** modelo V1 exportado y métricas documentadas.

---

### Semana 9 — Interfaz e inferencia

**Objetivo:** ejecutar el modelo desde una aplicación web.

**Actividades:**
- construir interfaz;
- habilitar acceso al micrófono;
- cargar modelo exportado;
- mostrar clase predicha;
- mostrar score de confianza;
- probar ejecución local.

**Responsable principal:** Diego  
**Apoyo:** Harold

**Criterio de cierre:** el navegador captura audio y devuelve una predicción.

---

### Semana 10 — Integración G1

**Objetivo:** completar el patrón Modelo → Lenguaje.

**Actividades:**
- formalizar tabla de criticidad;
- aplicar umbrales iniciales;
- configurar system prompt;
- conectar modelo con G1;
- manejar baja confianza;
- probar alertas esperadas.

**Responsables principales:** Diego y Jennifer  
**Apoyo:** Harold

**Criterio de cierre:** la predicción del modelo termina en una alerta comprensible.

---

### Semana 11 — Despliegue público

**Objetivo:** cumplir el requisito de acceso por URL.

**Actividades:**
- desplegar aplicación;
- verificar permisos de micrófono;
- probar desde otro dispositivo;
- revisar errores;
- documentar instrucciones de uso.

**Responsable principal:** Diego  
**Apoyo:** equipo completo

**Criterio de cierre:** un tercero puede abrir y usar el MVP sin intervención técnica.

---

### Semana 12 — Validación

**Objetivo:** probar el MVP en condiciones controladas con usuarios.

**Diseño:**
- 5 usuarios;
- 10 eventos por usuario;
- 50 observaciones.

**Registrar:**
- evento;
- detección correcta/incorrecta;
- tiempo de reacción;
- comprensión de alerta;
- falsos positivos/falsos negativos;
- comentarios;
- casos límite.

**Responsable principal:** Jennifer  
**Apoyo:** Harold y Diego

**Criterio de cierre:** evidencia documentada de 50 observaciones.

---

### Semana 13 — Reentrenamiento, resultados y riesgos

**Objetivo:** cumplir A3 y preparar evidencia final.

**Actividades:**
- seleccionar clases con peor desempeño;
- recolectar 15–20 audios adicionales por clase problemática;
- entrenar V2;
- comparar V1 vs. V2;
- evaluar KRs;
- documentar riesgos técnicos, éticos y legales;
- actualizar documentación.

**Responsables principales:** Harold y Jennifer  
**Apoyo:** Diego

**Meta A3:** mejorar al menos 5 puntos porcentuales de recall en la clase priorizada.

**Criterio de cierre:** V2 evaluada y resultados documentados.

---

### Semana 14 — PC2

**Objetivo:** demostrar el MVP en vivo.

**Actividades:**
- demo por URL pública;
- presentar métricas reales;
- explicar resultados;
- presentar riesgos y mitigaciones;
- responder preguntas.

**Responsable:** equipo completo.

---

## 5. Responsabilidades resumidas

| Entregable / tarea | Harold | Diego | Jennifer |
|---|:---:|:---:|:---:|
| Dataset | **R** | A | A |
| Licencias y fuentes | A | — | **R** |
| Modelo V1/V2 | **R** | A | — |
| Métricas del modelo | **R** | A | A |
| Interfaz web | A | **R** | A |
| Captura de audio | A | **R** | — |
| Integración G1 | A | **R** | **R** |
| Prompt | — | A | **R** |
| Despliegue | A | **R** | A |
| Validación de usuarios | A | A | **R** |
| Resultados OKR | **R** | A | **R** |
| Riesgos y ética | A | A | **R** |
| Sustentación | **R** | **R** | **R** |

**R = Responsable principal**  
**A = Apoyo**

---

## 6. Hitos de control

| Hito | Semana | Evidencia |
|---|---:|---|
| Propuesta cerrada | 5 | Plantillas + README + resumen + cronograma |
| PC1 | 6 | Presentación y repositorio |
| Dataset real listo | 7 | Carpetas + registro de fuentes |
| Modelo V1 | 8 | Modelo + métricas |
| Prototipo local | 9 | Clasificación desde navegador |
| Integración completa | 10 | Modelo + G1 |
| MVP público | 11 | URL |
| Validación | 12 | 5 usuarios / 50 observaciones |
| Modelo V2 + resultados | 13 | Comparación V1–V2 |
| PC2 | 14 | Demo en vivo |

---

## 7. Semanas 15–18

La guía del proyecto ubica la sustentación final del MVP en la **Semana 14**. Dado que el ciclo académico indicado por el equipo continúa hasta la **Semana 18**, estas semanas se consideran fuera del cronograma principal de construcción exigido para el proyecto, salvo que el docente asigne actividades adicionales, correcciones o cierre académico.

---

*Framework PROMPT v2.0 — AD5018 Inteligencia Artificial para Negocios*
