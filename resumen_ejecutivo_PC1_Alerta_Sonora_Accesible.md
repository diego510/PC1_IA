# Resumen Ejecutivo
## Proyecto Integrador de IA para Negocios — AD5018
### MVP: Alerta Sonora Accesible

**Equipo:** Harold Inca · Diego Requena · Jennifer Patiño  
**Semana actual:** 5  
**Hito próximo:** PC1 — Semana 6

---

## Problema y usuario

El proyecto aborda una necesidad de accesibilidad de **personas con discapacidad auditiva total o parcial** que pasan tiempo solas en el hogar o se desplazan por espacios cotidianos sin una persona oyente cerca.

El problema central es que muchos eventos importantes del entorno se comunican principalmente mediante señales acústicas. Como resultado, una persona con acceso limitado o nulo al canal auditivo puede no identificar oportunamente sonidos como una alarma, un detector de humo, un timbre o una bocina, lo que puede retrasar su reacción frente a eventos relevantes y reducir su autonomía.

Para estructurar la propuesta en PC1 se utilizará un **baseline académico provisional** de:

- **40 % de identificación correcta** de eventos sin apoyo del MVP.
- **6 segundos de tiempo promedio de reacción.**

Estos valores son provisionales y deberán sustituirse por resultados reales cuando se realice la validación.

---

## Solución propuesta

El MVP, denominado **Alerta Sonora Accesible**, busca detectar un conjunto acotado de sonidos del entorno y convertirlos en alertas visuales/textuales comprensibles.

El producto integra dos componentes:

### Componente analítico — A3
Un modelo de **clasificación de audio** entrenado por el equipo que distingue cinco clases:

- alarma;
- detector de humo;
- timbre;
- bocina;
- ruido de fondo.

La estrategia A3 consiste en entrenar una primera versión, analizar errores, recolectar nuevos datos en los casos problemáticos y reentrenar para medir la mejora.

### Componente generativo — G1
Una capa de lenguaje con contexto fijo que recibe:

- clase predicha;
- score de confianza;
- criticidad;
- umbral.

Con esa información genera una alerta breve, accesible y proporcional al nivel de certeza. Si la confianza es insuficiente, el sistema comunica incertidumbre en lugar de afirmar que el evento ocurrió.

**Patrón de conexión:** Modelo → Lenguaje.

---

## Datos

El dataset inicial propuesto está compuesto por **260 muestras de audio**:

| Clase | Muestras |
|---|---:|
| Alarma | 50 |
| Detector de humo | 50 |
| Timbre | 50 |
| Bocina | 50 |
| Ruido de fondo | 60 |
| **Total** | **260** |

Las fuentes previstas son Freesound.org, Pixabay Audio, Zapsplat y grabaciones propias.

La Fase R aún requiere completar la recolección real, verificar el número final por clase y documentar fuente y licencia de los audios externos.

---

## Métricas y objetivos

El baseline técnico estimado para un clasificador ingenuo que siempre predice la clase mayoritaria es **23.1 % de accuracy**.

Las metas propuestas para el MVP son:

- **≥ 80 %** de eventos críticos identificados correctamente;
- **≤ 3 segundos** de tiempo promedio de reacción;
- **≥ 80 %** de accuracy global;
- **≥ 85 %** de recall en alarma y detector de humo;
- mejora de **≥ 5 puntos porcentuales de recall** después del reentrenamiento A3;
- **≥ 90 %** de respuestas correctas y comprensibles en 20 casos de prueba de la capa G1.

---

## Validación

La validación se plantea con un alcance manejable para el curso:

- **5 usuarios**;
- **10 eventos por usuario**;
- **50 observaciones totales**.

Se registrará si cada evento fue identificado correctamente, el tiempo de reacción, la comprensión de la alerta y los errores observados.

Las **260 muestras corresponden a audios de entrenamiento**, no a personas participantes.

---

## Alcance y despliegue

El MVP incluirá captura de audio desde el micrófono, clasificación de cinco categorías, score de confianza, umbrales, alertas visuales/textuales, capa G1, expresión de incertidumbre, interfaz web, reentrenamiento A3 y despliegue mediante URL pública.

No incluirá reconocimiento ilimitado de sonidos, llamadas automáticas a emergencias, geolocalización, almacenamiento permanente de audio, aplicación móvil nativa, wearables, RAG ni agentes autónomos.

El stack propuesto es:

- **Teachable Machine** para el modelo;
- **TensorFlow.js** para inferencia;
- **Web Audio API** para captura de audio;
- **HTML/CSS/JavaScript** para la interfaz;
- **API de un modelo de lenguaje** para G1;
- **función serverless** para proteger credenciales;
- **Vercel** para despliegue;
- **GitHub** para repositorio y documentación.

---

## Estado actual

En la Semana 5, el proyecto ya cuenta con:

- problema y usuario definidos;
- niveles A3 + G1;
- patrón Modelo → Lenguaje;
- alcance del MVP;
- diseño inicial de datos;
- métricas y OKRs;
- flujo del producto;
- stack propuesto;
- plan de validación.

Antes de la PC1 se debe cerrar la recolección real de audios, documentar licencias, verificar técnicamente el stack y consolidar el cronograma y la presentación.

---

*Framework PROMPT v2.0 — AD5018 Inteligencia Artificial para Negocios*
