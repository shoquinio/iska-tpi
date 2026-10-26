# Entrega 4 – Mecanismos de control: indicadores y estándares de desempeño

El control cierra el proceso administrativo (planificación → organización → dirección → **control**). Se aplica en cuatro pasos: **1)** fijar el estándar, **2)** medir el desempeño real, **3)** comparar contra el estándar y **4)** corregir el desvío. Los estándares salen de las metas cuantitativas de la Entrega 2 y los datos se toman de las entidades del diccionario de la Entrega 3, así cada indicador es medible desde el propio sistema.

## A. Indicadores de auditoría técnica del sistema

| # | Indicador | Fórmula / medición | Estándar | Frecuencia | Fuente |
|---|---|---|---|---|---|
| T1 | Latencia de lectura | Tiempo entre lectura de la sonda y su visualización (percentil 95) | ≤ 1,5 s | Diaria (automática) | Log de lecturas |
| T2 | Disponibilidad | Horas operativas / horas de producción × 100 | ≥ 99 % mensual | Mensual | Monitor de servicio |
| T3 | Lecturas perdidas | (Lecturas esperadas − registradas) / esperadas × 100 | ≤ 0,5 % | Semanal | Log de lecturas |
| T4 | Tiempo de consulta del histórico | Tiempo de respuesta de un reporte de 3 años de lotes | ≤ 2 s | Trimestral | Prueba de carga |
| T5 | Respaldo verificado | Copias diarias restauradas con éxito / copias realizadas | 100 % | Mensual | Registro de backups |
| T6 | Incidentes críticos | Fallas que impiden registrar lotes o temperaturas; tiempo hasta resolverlas | 0 abiertos; resolución ≤ 48 h | Continua | Issues de GitHub (`bug`) |

## B. Indicadores de gestión que el sistema habilita

| # | Indicador | Fórmula | Estándar | Frecuencia | Entidad |
|---|---|---|---|---|---|
| G1 | Lotes rechazados | Lotes con `aprobado_calidad = false` / lotes elaborados × 100 | ≤ 5 % | Mensual | `LOTE_PRODUCCION` |
| G2 | Alarmas atendidas a tiempo | Alarmas confirmadas en ≤ 10 min / alarmas emitidas × 100 | ≥ 95 % | Semanal | Registro de alarmas |
| G3 | Quiebres de stock | Lotes demorados por falta de insumo | 0 por mes | Mensual | `MATERIA_PRIMA` |
| G4 | Exactitud de inventario | \|stock del sistema − conteo físico\| / conteo físico × 100 | ≤ 2 % | Mensual (inventario físico) | `MATERIA_PRIMA` |
| G5 | Cumplimiento del preventivo | Órdenes preventivas cerradas en fecha / programadas × 100 | ≥ 90 % | Mensual | `ORDEN_MANTENIMIENTO` |
| G6 | Parada no programada | Σ `horas_parada` de órdenes correctivas | ≤ 4 h por mes | Mensual | `ORDEN_MANTENIMIENTO` |

## Semáforo y acción correctiva

- 🟢 **Dentro del estándar:** se registra y no se actúa.
- 🟡 **Desvío leve** (hasta 10 % fuera del estándar): el responsable del área analiza la causa en la reunión semanal de producción.
- 🔴 **Desvío grave:** se abre un *issue* en el repositorio (si es técnico) o una orden de mantenimiento / acción de calidad (si es operativo) y la Dirección General decide la medida.

## Tipos de control aplicados

| Tipo | Ejemplo en Iska |
|---|---|
| **Preventivo** (antes) | Verificación de stock antes de elaborar; órdenes preventivas que evitan que un fermentador falle. |
| **Concurrente** (durante) | Monitoreo de temperatura con alarma en tiempo real durante la fermentación. |
| **Retroalimentación** (después) | Análisis de calidad del lote terminado y tablero mensual de indicadores que ajusta recetas y el plan de mantenimiento. |

## Responsables

| Indicadores | Responsable de medir | Recibe el informe |
|---|---|---|
| T1–T6 | Desarrollador del sistema | Dirección General |
| G1, G2 | Maestro Cervecero | Dirección General |
| G3, G4 | Resp. de Administración y Compras | Dirección General |
| G5, G6 | Asistente / Operario (Mantenimiento) | Maestro Cervecero |

## Auditoría técnica

Cada trimestre se revisa: que los indicadores T1–T6 se calculen desde datos reales (no cargados a mano), que cada cambio en `main` haya entrado por Pull Request revisado, que las historias del tablero coincidan con los commits que las referencian, y que los permisos de usuario respeten el organigrama (por ejemplo, sólo el maestro cervecero puede aprobar un lote).
