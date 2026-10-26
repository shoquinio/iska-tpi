# Entrega 4 – Backlog ágil e historias de usuario

El backlog se gestiona en **GitHub Projects** (vista tablero) con tres columnas: **Por hacer**, **En progreso** y **Listo**. Cada historia es un *issue* del repositorio con la etiqueta `historia-usuario`; los commits y Pull Requests lo referencian con `#número`, de modo que el tablero muestra qué trabajo del repositorio corresponde a cada historia.

## HU-01 – Alarma de temperatura de fermentación

> **Como** maestro cervecero, **quiero** ver en tiempo real la temperatura de cada fermentador y recibir una alarma cuando salga del rango de la receta, **para** corregir a tiempo y no perder el lote.

**Criterios de aceptación**
- La lectura de cada sonda PT-100 se muestra en pantalla en menos de 1,5 s.
- Si la temperatura se aparta más de ±1 °C del valor de la receta, el sistema emite una alarma visible y sonora.
- Cada alarma queda registrada con fecha, fermentador, valor y quién la atendió.

**Proceso BPMN:** compuerta *¿Temperatura en rango?* → alarma → *Corregir temperatura*.
**Estado en el tablero:** ✅ Listo

## HU-02 – Aviso de stock mínimo y orden de compra

> **Como** responsable de administración y compras, **quiero** que el sistema me avise cuando un insumo llega al stock mínimo y me proponga la orden de compra, **para** que la producción no se frene por falta de malta, lúpulo o levadura.

**Criterios de aceptación**
- Al crear un lote, el sistema descuenta los insumos de la receta.
- Si `stock_actual` < `stock_minimo`, se genera una orden de compra sugerida con la cantidad faltante.
- Al registrar el ingreso de mercadería, el stock se actualiza y la alerta se cierra.

**Proceso BPMN:** compuerta *¿Stock suficiente?* → *Aprobar y enviar orden de compra* → *Recibir insumos*.
**Estado en el tablero:** 🔄 En progreso

## HU-03 – Plan de mantenimiento preventivo

> **Como** asistente / operario de mantenimiento, **quiero** que el sistema me genere las órdenes de mantenimiento preventivo según la frecuencia definida para cada equipo, **para** evitar paradas no programadas de los fermentadores durante la producción.

**Criterios de aceptación**
- Cuando `fecha_ultimo_mant` + `frecuencia_preventivo_dias` llega a la fecha actual, se crea una `ORDEN_MANTENIMIENTO` de tipo Preventivo.
- Un equipo con una orden abierta figura como *fuera de servicio* y no puede asignarse a un lote nuevo.
- Al cerrar la orden se registran horas de parada y costo.

**Proceso BPMN:** sostiene la tarea *Corregir temperatura / revisar equipo* y la disponibilidad de fermentadores.
**Estado en el tablero:** 📋 Por hacer

## Seguimiento

| Historia | Issue | Rama | Estado |
|---|---|---|---|
| HU-01 | #1 | `feature/bpmn-proceso-lote` | Listo |
| HU-02 | #2 | `feature/backlog-historias-usuario` | En progreso |
| HU-03 | #3 | `feature/indicadores-control` | Por hacer |
