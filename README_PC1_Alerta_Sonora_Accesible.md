# Alerta Sonora Accesible
## Proyecto Integrador de IA para Negocios — AD5018
### Universidad de Ingeniería y Tecnología (UTEC)

---

## 1. Información del equipo

**Integrantes**
- Harold Inca
- Diego Requena
- Jennifer Patiño

**Curso:** AD5018 — Inteligencia Artificial para Negocios  
**Framework:** PROMPT v2.0  
**Semana actual:** Semana 5  
**Próximo hito:** PC1 — Semana 6  
**Fin del ciclo académico:** Semana 18  
**Estado del proyecto:** En diseño y preparación para PC1

---

## 2. Nombre del MVP

**Alerta Sonora Accesible**

---

## 3. Resumen del proyecto

Alerta Sonora Accesible es un MVP orientado a personas con discapacidad auditiva que pueden tener dificultad para identificar oportunamente sonidos relevantes de su entorno.

El proyecto busca detectar un conjunto acotado de eventos acústicos —alarma, detector de humo, timbre, bocina y ruido de fondo— mediante un modelo de clasificación de audio entrenado por el equipo. El resultado del modelo se conecta con una capa de lenguaje que transforma la clase detectada, el nivel de confianza y la criticidad del evento en una alerta visual/textual breve y comprensible.

El proyecto combina:

- **Componente analítico A3:** clasificación de audio con reentrenamiento a partir de errores observados.
- **Componente generativo G1:** prompt con contexto fijo para convertir la salida del modelo en una alerta accesible.
- **Patrón de conexión:** Modelo → Lenguaje.

---

## 4. Problema

Las personas con discapacidad auditiva que permanecen solas en el hogar o se desplazan por espacios cotidianos tienen dificultad para identificar oportunamente eventos del entorno comunicados principalmente mediante señales acústicas —como alarmas, detectores de humo, timbres o bocinas— debido a su acceso limitado o nulo al canal auditivo, lo que incrementa la posibilidad de no reaccionar oportunamente ante eventos relevantes y reduce su autonomía.

---

## 5. Usuario objetivo

Personas con discapacidad auditiva total o parcial que:

- pasan periodos de tiempo sin una persona oyente cerca;
- necesitan reconocer sonidos relevantes del entorno;
- pueden utilizar un dispositivo con navegador y micrófono;
- requieren una señal visual/textual como alternativa al canal auditivo.

---

## 6. Propuesta de valor

Detectar sonidos relevantes del entorno y convertirlos en alertas visuales/textuales comprensibles, indicando el nivel de certeza de la detección y evitando presentar como seguro aquello que el modelo no reconoce con suficiente confianza.

---

## 7. Alcance del MVP

### Incluye

- captura de audio desde el micrófono;
- clasificación de cinco categorías:
  - alarma;
  - detector de humo;
  - timbre;
  - bocina;
  - ruido de fondo;
- score de confianza;
- umbrales iniciales por clase;
- clasificación de criticidad;
- alerta visual/textual;
- capa generativa G1;
- expresión de incertidumbre en casos de baja confianza;
- interfaz web;
- despliegue mediante URL pública;
- reentrenamiento del modelo para cumplir el nivel A3;
- validación con usuarios y registro de resultados.

### No incluye

- reconocimiento ilimitado de cualquier sonido;
- llamadas automáticas a servicios de emergencia;
- geolocalización;
- almacenamiento permanente de audio;
- reconocimiento o transcripción de conversaciones;
- aplicación móvil nativa;
- integración con wearables;
- RAG;
- agentes autónomos;
- automatizaciones G4.

---

## 8. Diseño de IA

### Componente analítico — A3

El modelo clasificará fragmentos de audio en cinco categorías:

```text
alarma
detector_humo
timbre
bocina
ruido_de_fondo
```

La estrategia A3 será:

1. entrenar una primera versión del modelo;
2. medir su desempeño;
3. analizar errores y clases problemáticas;
4. recolectar nuevas muestras dirigidas a esos errores;
5. reentrenar;
6. comparar V1 vs. V2.

### Componente generativo — G1

La capa G1 recibe:

```text
clase predicha + score de confianza + criticidad + umbral
```

y genera una alerta breve, clara y proporcional al nivel de confianza.

### Flujo

```text
Micrófono
   ↓
Audio
   ↓
Modelo de clasificación A3
   ↓
Clase + score de confianza
   ↓
Criticidad + umbral
   ↓
Capa G1
   ↓
Alerta visual/textual
   ↓
Usuario
```

---

## 9. Datos

### Dataset inicial propuesto

| Clase | Muestras de audio objetivo |
|---|---:|
| Alarma | 50 |
| Detector de humo | 50 |
| Timbre | 50 |
| Bocina | 50 |
| Ruido de fondo | 60 |
| **Total** | **260** |

> **Importante:** las 260 observaciones corresponden a muestras de audio para entrenar el modelo, no a personas participantes.

### Fuentes previstas

- Freesound.org
- Pixabay Audio
- Zapsplat
- grabaciones propias

La trazabilidad de fuentes, licencias y disponibilidad se documenta en la Plantilla 2.

---

## 10. Métricas y OKRs propuestos

Para estructurar la PC1 se utilizan valores académicos provisionales que deberán sustituirse por resultados reales cuando se disponga de evidencia.

| Indicador | Baseline / referencia | Meta |
|---|---:|---:|
| Identificación correcta de eventos | 40 % provisional | ≥ 80 % |
| Tiempo promedio de reacción | 6 s provisional | ≤ 3 s |
| Baseline técnico de clase mayoritaria | 23.1 % accuracy | Superarlo ampliamente |
| Accuracy global del modelo | — | ≥ 80 % |
| Recall en alarma | — | ≥ 85 % |
| Recall en detector de humo | — | ≥ 85 % |
| Mejora después del reentrenamiento | V1 | ≥ +5 pp de recall en la clase priorizada |
| Calidad del componente G1 | — | ≥ 90 % de 20 casos de prueba |

---

## 11. Validación propuesta

La validación del MVP se realizará con una muestra pequeña y manejable acorde al alcance de un proyecto universitario:

- **5 usuarios**
- **10 eventos por usuario**
- **50 observaciones totales**

Se registrará:

- evento presentado;
- si fue identificado correctamente;
- tiempo de reacción;
- comprensión de la alerta;
- errores observados;
- comentarios del usuario.

---

## 12. Stack tecnológico propuesto

| Capa | Tecnología |
|---|---|
| Entrenamiento del modelo | Teachable Machine — Audio |
| Inferencia | TensorFlow.js |
| Captura de audio | Web Audio API |
| Interfaz | HTML / CSS / JavaScript |
| Capa G1 | API de un modelo de lenguaje con prompt fijo |
| Backend | Función serverless |
| Despliegue | Vercel |
| Repositorio | GitHub |

El stack deberá ser verificado mediante una prueba técnica antes de considerarse definitivo.

---

## 13. Estado del proyecto — Semana 5

### Completado

- [x] Definición del usuario.
- [x] Definición del problema.
- [x] Causa raíz.
- [x] Consecuencia medible planteada.
- [x] Elección de A3 + G1.
- [x] Patrón Modelo → Lenguaje.
- [x] Alcance preliminar del MVP.
- [x] Inventario inicial de datos.
- [x] Diseño preliminar del flujo.
- [x] Definición inicial de métricas.
- [x] Propuesta de stack.
- [x] Plan preliminar de validación.

### Por cerrar antes de PC1

- [ ] Completar la recolección real de audios.
- [ ] Registrar el número final de muestras por clase.
- [ ] Documentar licencias y fuentes de los audios.
- [ ] Verificar técnicamente el stack.
- [ ] Formalizar la tabla de criticidad.
- [ ] Confirmar los umbrales iniciales.
- [ ] Completar el resumen ejecutivo.
- [ ] Completar el cronograma de construcción.
- [ ] Preparar la presentación de PC1.
- [ ] Revisar que todos los integrantes puedan explicar cualquier fase de la propuesta.

---

## 14. Estructura del repositorio

```text
/
├── README.md
├── resumen_ejecutivo.md
├── presentacion_pc1.pdf
├── cronograma.md
│
├── plantillas/
│   ├── plantilla_1_problem_statement.md
│   ├── plantilla_2_data_readiness.md
│   └── plantilla_3_ai_product_canvas.md
│
├── datos/
│   ├── alarma/
│   ├── detector_humo/
│   ├── timbre/
│   ├── bocina/
│   └── ruido_de_fondo/
│
└── evidencia/
    ├── fuentes_datos.md
    ├── licencias_audios.md
    └── pruebas_stack.md
```

---

## 15. Próximos pasos

### Semana 5
- cerrar las tres plantillas de PC1;
- organizar y documentar el dataset;
- verificar acceso a las herramientas;
- construir el resumen ejecutivo;
- elaborar el cronograma.

### Semana 6
- entregar PC1;
- sustentar problema, datos, producto, stack y plan de construcción;
- dejar congelados los niveles A3 + G1, el patrón de conexión y los KRs comprometidos.

### Después de PC1
- construir la primera versión del modelo;
- integrar la capa G1;
- desarrollar la interfaz web;
- desplegar una primera versión pública;
- evaluar V1;
- recolectar nuevos datos;
- reentrenar V2;
- validar con usuarios;
- medir resultados y documentar riesgos.

> Aunque el ciclo académico termina en la **Semana 18**, el cronograma operativo del proyecto debe seguir los hitos específicos definidos por la guía del curso para PC1 y PC2.

---

## 16. Documentos principales

- `plantillas/plantilla_1_problem_statement.md` — Fase P
- `plantillas/plantilla_2_data_readiness.md` — Fase R
- `plantillas/plantilla_3_ai_product_canvas.md` — Fase O
- `resumen_ejecutivo.md` — síntesis de P + R + O
- `cronograma.md` — plan de construcción y responsables
- `presentacion_pc1.pdf` — sustentación de la propuesta

---

**Estado actual:** Preparación de PC1 — Semana 5.
