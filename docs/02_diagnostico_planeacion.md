# Entrega 2 – Diagnóstico y planeación del proyecto de software (versión corregida)

## FODA del proyecto

| Fortalezas (internas) | Oportunidades (externas) |
|---|---|
| Conocimiento técnico del proceso cervecero y del mantenimiento de planta unido a las competencias de desarrollo. Dominio de JavaScript, GitHub y Postman. Acceso directo a la planta (PLC, sondas PT-100, caudalímetros) para probar en vivo. | Sensores y hardware open source de bajo costo integrables por API. Ecosistema de software libre sin costo de licencias. Protocolos industriales abiertos para integrar el PLC. Posibilidad de escalar el sistema como producto para las 7 cervecerías artesanales de Jujuy. |
| **Debilidades (internas)** | **Amenazas (externas)** |
| Un solo desarrollador: las tareas no pueden ejecutarse en paralelo. Recursos limitados para servidores propios (dependencia inicial de la nube). Cruce entre horas de programación y turnos de planta. | Costos de importación y tipo de cambio del hardware. Cortes de energía que afecten servidor, toma de datos y panel. Dependencia de proveedores de nube (precios en dólares, conectividad). Protocolos propietarios o poco documentados de algunos equipos. |

**Estrategias:** FO – probar sensores open source con datos reales desde el inicio; DO – software libre y nube de bajo costo en lugar de servidores propios; FA – reutilizar el hardware instalado y elegir componentes de provisión local; DA – almacenamiento local de lecturas ante cortes y una semana de reserva en el cronograma.

## Objetivo general

Diseñar, desarrollar e implementar, en un plazo de 10 semanas, un sistema de software integral para la automatización de procesos, el control en tiempo real de las variables de elaboración y la gestión del mantenimiento predictivo de los equipos de la microcervecería Iska.

## Metas cuantitativas

1. **Tiempo de respuesta:** procesar las lecturas PT-100 de los 8 fermentadores y actualizar la interfaz en menos de **1,5 s** desde que se toma la lectura.
2. **Escalabilidad:** almacenar al menos **80 millones de registros** (3 años con margen: 8 sensores × 1 lectura cada 10 s = 69.120 registros/día) y responder la consulta del historial de un fermentador de 30 días (259.200 lecturas) en menos de **2 s**.
3. **Mantenimiento predictivo:** registrar el 100 % de las horas de funcionamiento de bombas y equipo de frío y alertar cuando un equipo llegue al **90 % de su intervalo** de mantenimiento o un fermentador tarde **más de un 20 %** sobre su promedio en alcanzar la temperatura objetivo.
4. **Plazo:** versión 1.0 en producción en **10 semanas** (9 de trabajo + 1 de reserva de contingencia).

## Planificación (Gantt) – secuencial, responsable: Cristian Chocobar

| Tarea | Duración | Precede | Semana |
|---|---|---|---|
| T1 Análisis de requisitos | 1 sem | – | S1 |
| T2 Diseño del sistema | 1 sem | T1 | S2 |
| T3 Codificación backend | 2 sem | T2 | S3–S4 |
| T4 Codificación módulo de mantenimiento predictivo | 1 sem | T3 | S5 |
| T5 Codificación frontend | 2 sem | T4 | S6–S7 |
| T6 Pruebas de calidad (QA) | 1 sem | T5 | S8 |
| T7 Implementación | 1 sem | T6 | S9 |
| R Reserva de contingencia | 1 sem | T7 | S10 |
