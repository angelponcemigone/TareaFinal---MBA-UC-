# Agente de Evaluación de Propuestas — Procurement

## Descripción

Este repositorio contiene la estructura base de un **agente de IA para
evaluación de propuestas de proveedores** en un área de Procurement. El
agente apoya al equipo de compras en la recepción, análisis técnico,
análisis comercial/financiero, ranking y generación de informes para
procesos de licitación (RFP/RFQ), además de monitorear plazos y emitir
alertas.

El agente **no reemplaza el criterio del comprador**: automatiza tareas
repetitivas de análisis y consolidación de información, dejando la
decisión final y la validación de resultados en manos del equipo humano
de Procurement.

## Propósito

- Estandarizar y acelerar la evaluación de propuestas técnicas y
  comerciales.
- Reducir el riesgo de error humano al consolidar información de
  múltiples proveedores.
- Generar un ranking objetivo y trazable, basado en pesos y criterios
  definidos previamente por la organización.
- Producir informes de evaluación listos para revisión y aprobación.
- Monitorear plazos del proceso y alertar sobre riesgos de
  incumplimiento (SLA, vencimientos, hitos).

## Estructura de carpetas

```
agente-procurement/
├── README.md                       # Este documento
├── config/
│   └── parametros.yaml             # Pesos, SLA mínimos, umbrales y parámetros del proceso
├── prompts/
│   ├── 01_ingesta.md               # Recepción y validación de documentos
│   ├── 02_analisis_tecnico.md      # Scorecard técnico
│   ├── 03_analisis_comercial.md    # Análisis comercial y financiero
│   ├── 04_ranking.md               # Ranking ponderado y shortlist
│   ├── 05_informe.md               # Generación de informe final
│   └── 06_monitoreo.md             # Monitoreo de plazos y alertas
├── plantillas/
│   ├── scorecard_tecnico.xlsx      # Plantilla de evaluación técnica (vacía)
│   ├── comparativo_comercial.xlsx  # Plantilla de análisis comercial (vacía)
│   └── informe_evaluacion.docx     # Plantilla de informe final (vacía)
├── documentos/
│   ├── bases/                      # Bases de licitación (RFP/RFQ)
│   ├── propuestas/                 # Propuestas recibidas de proveedores
│   └── internos/                   # Minutas y lineamientos internos
├── outputs/                        # Informes y salidas generadas por el agente
└── logs/
    └── auditoria.md                # Registro de acciones del agente
```

## Instrucciones de uso

1. **Configurar parámetros**: editar `config/parametros.yaml` con los
   pesos de evaluación, SLA mínimos por categoría y umbrales de alerta
   que apliquen al proceso de compra vigente.
2. **Cargar documentos**: depositar las bases de licitación en
   `documentos/bases/`, las propuestas de proveedores en
   `documentos/propuestas/` y cualquier minuta o lineamiento interno en
   `documentos/internos/`.
3. **Ejecutar los prompts en orden** (carpeta `prompts/`), usando el
   agente/LLM de preferencia, siguiendo la secuencia 01 → 06.
4. **Usar las plantillas**: los prompts de análisis técnico y comercial
   completan las plantillas de `plantillas/` (scorecard técnico y
   comparativo comercial); el prompt de informe completa
   `informe_evaluacion.docx`.
5. **Revisar las salidas**: los resultados generados (scorecards
   completos, comparativos, informes) se guardan en `outputs/`.
6. **Auditoría**: cada acción relevante del agente debe quedar
   registrada en `logs/auditoria.md`.

## Flujo de trabajo resumido (6 pasos)

1. **Ingesta**: el agente recibe y valida que las bases y propuestas
   estén completas y en el formato esperado (`01_ingesta.md`).
2. **Análisis técnico**: evalúa cada propuesta contra los criterios
   técnicos definidos y genera el scorecard técnico
   (`02_analisis_tecnico.md`).
3. **Análisis comercial**: evalúa precio, condiciones de pago, plazos
   de entrega y otros factores comerciales/financieros
   (`03_analisis_comercial.md`).
4. **Ranking**: combina los puntajes técnico y comercial según los
   pesos definidos y genera un ranking ponderado y shortlist
   (`04_ranking.md`).
5. **Informe**: consolida los resultados en un informe final de
   evaluación listo para revisión (`05_informe.md`).
6. **Monitoreo**: hace seguimiento a los plazos del proceso y emite
   alertas tempranas ante riesgos de incumplimiento
   (`06_monitoreo.md`).

## Estado

Estructura base creada. Pendiente: cargar documentos reales del
proceso de compra y ajustar `parametros.yaml` a los criterios
definitivos de la organización.
