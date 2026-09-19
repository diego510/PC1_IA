# Plantilla 3 — AI Product Canvas
## Framework PROMPT | Fase O — Diseño del Producto
### AD5018 Inteligencia Artificial para Negocios | UTEC

---

**Equipo:**
- Integrante 1: Harold Inca
- Integrante 2: Diego Requena
- Integrante 3: Jennifer Patiños

**Fecha de entrega:** 18/09/2026
**Versión:**

---

# SECCIÓN 1 — AI Product Canvas

## 1.1 Nombre del MVP

**Alerta Sonora Accesible**

## 1.2 Problema

Las personas con discapacidad auditiva que permanecen solas en el hogar o se desplazan por espacios cotidianos tienen dificultad para identificar oportunamente eventos del entorno comunicados principalmente mediante señales acústicas —como alarmas, detectores de humo, timbres o bocinas— debido a su acceso limitado o nulo al canal auditivo, lo que incrementa la posibilidad de no reaccionar oportunamente ante eventos relevantes y reduce su autonomía.

## 1.3 Usuario objetivo

Personas con discapacidad auditiva total o parcial que pasan periodos de tiempo sin una persona oyente cerca y utilizan un dispositivo con navegador y micrófono.

## 1.4 Propuesta de valor

Detectar sonidos relevantes del entorno y convertirlos en alertas visuales/textuales comprensibles, indicando el nivel de certeza y evitando presentar como seguro aquello que el modelo no reconoce con suficiente confianza.

---

# SECCIÓN 2 — Componentes

## Analítico

**A3 — Clasificación de audio**

Clases:
- alarma
- detector_humo
- timbre
- bocina
- ruido_de_fondo

## Generativo

**G1 — Prompt con contexto fijo**

Entrada:
- clase;
- confianza;
- criticidad;
- umbral.

Salida:
- alerta breve;
- nivel de certeza;
- indicación de verificación cuando corresponda.

---

# SECCIÓN 3 — Flujo

```text
Micrófono
↓
Audio
↓
Modelo A3
↓
Clase + confianza
↓
Criticidad + umbral
↓
G1
↓
Alerta visual/textual
↓
Usuario
```

---

# SECCIÓN 4 — System Prompt

```text
Eres la capa de comunicación de un sistema de accesibilidad para personas
con discapacidad auditiva.

Recibirás una clase de sonido, un score de confianza, un nivel de criticidad
y un umbral.

Genera una alerta breve y clara.

Reglas:
- No inventes información.
- No afirmes un evento si la confianza está bajo el umbral.
- Comunica incertidumbre cuando corresponda.
- Prioriza claridad en eventos críticos.
- Máximo dos oraciones.
```

---

# SECCIÓN 5 — Model Design Canvas

## Dataset inicial

| Clase | Muestras |
|---|---:|
| Alarma | 50 |
| Detector de humo | 50 |
| Timbre | 50 |
| Bocina | 50 |
| Ruido de fondo | 60 |
| **Total** | **260 audios** |

> **260 corresponde a audios de entrenamiento, no a personas.**

## Baseline técnico

Clase mayoritaria:

**60 / 260 = 23.1 % de accuracy estimada.**

## Baseline de negocio provisional

- identificación correcta sin MVP: **40 %**;
- tiempo promedio de reacción: **6 segundos**.

Estos valores son estimaciones académicas provisionales para estructurar la PC1.

## Métricas

- recall por clase;
- precision por clase;
- accuracy;
- matriz de confusión.

## Metas técnicas

- accuracy global ≥ 80 %;
- recall de alarma ≥ 85 %;
- recall de detector_humo ≥ 85 %.

---

# SECCIÓN 6 — Umbrales

| Clase | Criticidad | Umbral inicial |
|---|---|---:|
| Detector de humo | Alta | 0.80 |
| Alarma | Alta | 0.80 |
| Bocina | Alta | 0.78 |
| Timbre | Media | 0.75 |
| Ruido de fondo | Baja | 0.70 |

---

# SECCIÓN 7 — OKRs

## Objetivo

Mejorar la capacidad del usuario para identificar oportunamente sonidos relevantes del entorno mediante un MVP accesible.

### KR1
Pasar de un baseline provisional de **40 %** de identificación correcta a **≥ 80 %**.

### KR2
Reducir el tiempo promedio de reacción de **6 segundos** a **≤ 3 segundos**.

### KR3
Superar el baseline técnico de **23.1 %** y alcanzar:
- accuracy ≥ 80 %;
- recall ≥ 85 % en alarma y detector_humo.

### KR4
Tras reentrenar, mejorar al menos **5 puntos porcentuales de recall** en la clase con peor desempeño.

### KR5
Lograr que **≥ 90 % de 20 casos de prueba G1** generen una alerta correcta y comprensible.

---

# SECCIÓN 8 — Validación con usuarios

La validación propuesta es:

- **5 usuarios**;
- **10 eventos por usuario**;
- **50 observaciones en total**.

Cada usuario probará una secuencia de eventos que combine las clases objetivo y ruido de fondo.

Se registrará:

- si el evento fue identificado;
- tiempo de reacción;
- tipo de error;
- comprensión de la alerta;
- observaciones del usuario.

> Este tamaño es apropiado para un MVP universitario y además supera el mínimo de 5 usuarios requerido por la rúbrica para aspirar al nivel excelente en validación.

---

# SECCIÓN 9 — Estrategia A3

1. Entrenar V1.
2. Evaluar errores.
3. Identificar clases problemáticas.
4. Recolectar 15–20 audios adicionales en esas clases.
5. Reentrenar.
6. Comparar V1 vs. V2.
7. Buscar mejora ≥ 5 pp de recall en la clase problemática.

---

# SECCIÓN 10 — Stack

| Capa | Tecnología |
|---|---|
| Modelo | Teachable Machine |
| Inferencia | TensorFlow.js |
| Audio | Web Audio API |
| Interfaz | HTML/CSS/JavaScript |
| G1 | API de LLM |
| Backend | Función serverless |
| Despliegue | Vercel |
| Repositorio | GitHub |

---

# SECCIÓN 11 — Alcance

## Incluye
- captura de audio;
- cinco clases;
- confianza;
- umbrales;
- alerta visual;
- G1;
- expresión de incertidumbre;
- URL pública;
- reentrenamiento A3;
- validación con 5 usuarios.

## No incluye
- reconocimiento ilimitado;
- llamadas automáticas de emergencia;
- geolocalización;
- almacenamiento permanente de audio;
- aplicación móvil nativa;
- wearables;
- RAG;
- agentes;
- automatizaciones.

---

# SECCIÓN 12 — Criterios de éxito

1. ≥ 80 % de eventos críticos identificados.
2. ≤ 3 segundos de reacción promedio.
3. accuracy ≥ 80 %.
4. recall ≥ 85 % en clases críticas.
5. mejora ≥ 5 pp tras reentrenamiento.
6. ≥ 90 % de casos G1 correctos.
7. URL pública funcional.
8. 5 usuarios completan la prueba.
9. 50 observaciones documentadas.

---

# SECCIÓN 13 — Resumen de cifras

| Elemento | Valor |
|---|---:|
| Audios de entrenamiento | 260 |
| Personas para validación | 5 |
| Eventos por persona | 10 |
| Observaciones humanas | 50 |
| Baseline técnico | 23.1 % |
| Baseline negocio provisional | 40 % |
| Tiempo base provisional | 6 s |
| Meta identificación | ≥ 80 % |
| Meta reacción | ≤ 3 s |
| Meta accuracy | ≥ 80 % |
| Meta recall crítico | ≥ 85 % |
| Mejora A3 | ≥ 5 pp |
| Casos G1 | 20 |
| Meta G1 | ≥ 90 % |
