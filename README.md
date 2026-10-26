# Sistema ISKA – Control de producción y mantenimiento de la microcervecería artesanal Iska

**Trabajo Práctico Integrador y Progresivo (TPI) – Organización Empresarial**
Tecnicatura Universitaria en Programación a Distancia (TUP AD) – Universidad Tecnológica Nacional

| | |
|---|---|
| **Integrante** | Cristian Daniel Chocobar |
| **Cátedra** | Prof. Gabriela Martínez (titular); Prof. Carolina Bruno, Prof. Mario Raúl López, Prof. Andrea Ramos (adjuntos) |
| **Tablero ágil** | GitHub Projects – *Backlog Sistema ISKA* (enlace en la sección [Enlaces](#enlaces)) |
| **Estado** | Entrega N.º 4 – Procesos, trabajo colaborativo y control integrador |

---

## Descripción del sistema

Iska es una microcervecería artesanal de Jujuy que elabora cerveza estilo Golden en botellas de 330 cm³, con una capacidad de 2.000 litros semanales y cuatro personas en su dotación (dueño, responsable de administración y compras, maestro cervecero y asistente/operario).

El **Sistema ISKA** es el software que se propone construir para la planta. Centraliza tres funciones que hoy se llevan en papel y planillas:

1. **Control de elaboración y fermentación:** registro de lotes, lectura de la temperatura de los fermentadores (sondas PT-100) y alarma cuando un valor sale de rango.
2. **Inventario de insumos y producto terminado:** descuento automático de malta, lúpulo, levadura, botellas y etiquetas por cada lote; aviso de stock mínimo y orden de compra sugerida.
3. **Mantenimiento de equipos:** órdenes de mantenimiento preventivo según la frecuencia de cada equipo y registro de paradas y correctivos.

El proceso de negocio que el sistema automatiza está modelado en BPMN en [`docs/04_proceso_bpmn.md`](docs/04_proceso_bpmn.md).

## Estructura del repositorio

```
iska-tpi/
├── README.md                      ← portada del proyecto (este archivo)
└── docs/
    ├── 01_caso_sistema_abierto.md      Entrega 1: caso, misión, visión y TGS
    ├── 02_diagnostico_planeacion.md    Entrega 2: FODA, objetivos, metas y Gantt
    ├── 03_estructura_y_datos.md        Entrega 3: organigrama y diccionario de datos
    ├── 04_proceso_bpmn.md              Entrega 4: proceso de negocio en BPMN
    ├── 05_backlog_historias_usuario.md Entrega 4: historias de usuario y tablero
    ├── 06_indicadores_control.md       Entrega 4: indicadores y estándares de control
    ├── bpmn/proceso_lote_iska.bpmn     modelo BPMN 2.0 (se abre en bpmn.io / Camunda Modeler)
    ├── bpmn/proceso_lote_iska.png      imagen del diagrama
    └── img/organigrama_iska.png
```

## Flujo de trabajo con Git

- `main` contiene sólo trabajo revisado. Nadie escribe directamente sobre `main`.
- Cada tarea se hace en una rama secundaria con prefijo: `docs/…` para documentación de entregas anteriores y `feature/…` para lo nuevo de la Entrega 4.
- Los mensajes de commit siguen la convención *Conventional Commits* (`docs:`, `feat:`, `fix:`) en español y en modo imperativo, explicando **qué** cambia.
- Toda rama entra a `main` mediante **Pull Request** con revisión de un par. El PR de `feature/indicadores-control` es el que se usa para evidenciar la revisión.
- Cada historia de usuario del tablero tiene un *issue* asociado; los commits y PR lo referencian (`#n`) para que el tablero muestre el avance.

## Enlaces

- Repositorio: https://github.com/shoquinio/iska-tpi
- Tablero GitHub Projects: https://github.com/users/shoquinio/projects/1

## Declaración de Uso de IA

Para esta entrega se utilizó el asistente **Claude (Anthropic)** a través de Claude Code. No se usó para decidir el contenido del caso: todos los datos de la cervecería (dotación, capacidad, equipos, sensores, días de producción, metas) salen de las Entregas 1 a 3 y del proyecto técnico propio sobre la planta.

**Prompts utilizados y para qué sirvieron**

| # | Prompt (resumido) | Propósito | Juicio crítico sobre el resultado |
|---|---|---|---|
| 1 | “Resolvé este TP respetando las consignas; podés ver los TP anteriores de la cervecería (antes RACER, ahora Iska)” | Ordenar las cuatro consignas y reutilizar lo ya entregado | La IA propuso automatizar el proceso de lote completo; se aceptó porque es el que conecta los tres módulos del sistema definidos en la Entrega 2. |
| 2 | Generación del diagrama BPMN (pools, lanes y compuertas) a partir del proceso de elaboración | Dibujar el diagrama y el archivo `.bpmn` | Se controló que cada tarea estuviera en el carril del puesto correcto según el organigrama y que las excepciones (falta de stock, temperatura fuera de rango, lote rechazado) usaran compuertas exclusivas. |
| 3 | Redacción de historias de usuario e indicadores de control | Primer borrador en formato formal | Los estándares numéricos se tomaron de las metas cuantitativas de la Entrega 2 (1,5 s de respuesta, 80 millones de registros con consulta en menos de 2 s, alerta predictiva al 90 % del intervalo, 10 semanas con reserva), no de valores genéricos propuestos por la IA. |

**Correcciones humanas sobre las respuestas de la IA**

- Se reemplazó el nombre anterior de la empresa (“RACER Pala Ale”) por **Iska** en todo el material reutilizado.
- Se detectaron diferencias entre entregas (estilo Golden / Pale Ale y ciudad de la planta) y se unificó el caso en *Iska, estilo Golden, Jujuy*.
- Se verificó que los nombres de entidades y campos usados en los indicadores existan en el diccionario de datos de la Entrega 3 (`LOTE_PRODUCCION`, `MATERIA_PRIMA`, `EQUIPO`, `ORDEN_MANTENIMIENTO`).
- Se revisó el BPMN con la notación de la cátedra: los pools externos (proveedor y cliente) se comunican sólo con flujos de mensaje, nunca con flujos de secuencia.
- *(Completar con las correcciones propias que se hagan al revisar el trabajo antes de entregarlo.)*

El autor asume la responsabilidad intelectual del contenido: cualquier error del modelo de lenguaje que haya quedado es un error propio.
