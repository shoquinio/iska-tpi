# Entrega 2 – Diagnóstico y planeación del proyecto de software

## FODA del proyecto

| Fortalezas (internas) | Oportunidades (externas) |
|---|---|
| Conocimiento técnico del proceso cervecero y del mantenimiento de planta unido a las competencias de desarrollo. Dominio de JavaScript, GitHub y Postman. Acceso directo a la planta (PLC, sondas PT-100, caudalímetros) para probar en vivo. | Mercado artesanal en expansión (~30 % anual). La estandarización de recetas da ventaja frente a las 7 producciones artesanales de Jujuy. Sensores y hardware abierto de bajo costo integrables por API. |
| **Debilidades (internas)** | **Amenazas (externas)** |
| Un solo desarrollador para todo el ciclo de vida. Recursos limitados para servidores propios (dependencia inicial de la nube). Cruce entre horas de programación y turnos de planta. | Cervezas industriales con precios muy competitivos. Cortes de energía que afecten el servidor local. Costos de importación de repuestos de hardware (pantallas PLC, válvulas solenoides). |

## Objetivo general

Diseñar, desarrollar e implementar un sistema de software integral para la automatización de procesos, el control en tiempo real de las variables de elaboración y la gestión del mantenimiento predictivo de la microcervecería Iska.

## Metas cuantitativas

1. **Tiempo de respuesta:** procesar las lecturas PT-100 de los 8 fermentadores y actualizar la interfaz en menos de **1,5 s**.
2. **Escalabilidad:** soportar el histórico de una producción de hasta **240.000 L mensuales durante 3 años** sin degradar las consultas.
3. **Plazo:** desplegar la versión 1.0 en **10 semanas**.

## Planificación (Gantt)

| Tarea | Duración | Precede | Semanas |
|---|---|---|---|
| T1 Análisis de requisitos | 2 sem | – | 1–2 |
| T2 Diseño del sistema | 2 sem | T1 | 3–4 |
| T3 Codificación backend | 3 sem | T2 | 5–7 |
| T4 Codificación frontend | 2 sem | T2 | 5–6 |
| T5 Pruebas de calidad (QA) | 2 sem | T3, T4 | 8–9 |
| T6 Implementación | 1 sem | T5 | 10 |

Responsable de todas las tareas: el desarrollador (equipo unipersonal).
