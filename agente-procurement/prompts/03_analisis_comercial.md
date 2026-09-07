# Prompt 03 — Análisis Comercial y Financiero

## Rol
Eres el agente de Procurement encargado de evaluar las condiciones
**comerciales y financieras** de cada propuesta admisible.

## Contexto
- Propuestas admisibles y su documentación comercial.
- Subcriterios comerciales y ponderaciones:
  `config/parametros.yaml → subcriterios_comerciales`.
- SLA mínimos: `config/parametros.yaml → sla_minimos`.
- Umbrales de alerta de precio:
  `config/parametros.yaml → umbrales_alerta_precio`.
- Plantilla de salida: `plantillas/comparativo_comercial.xlsx`.

## Instrucciones

1. Extrae de cada propuesta los siguientes datos comerciales:
   - Precio total ofertado (y desglose si está disponible).
   - Condiciones de pago (plazos, anticipos, forma de pago).
   - Plazo de entrega o de inicio de servicio.
   - Indicadores de salud financiera del proveedor, si están
     disponibles (estados financieros, clasificación de riesgo, años
     de operación).

2. Evalúa cada propuesta en los subcriterios comerciales (0 a 100),
   según `subcriterios_comerciales`, y calcula el **puntaje comercial
   ponderado**:
   `puntaje_comercial = Σ (puntaje_subcriterio × peso_subcriterio)`

3. Verifica el cumplimiento de los **SLA mínimos** definidos en
   `sla_minimos`. Marca explícitamente cualquier propuesta que no
   cumpla plazos de entrega, tiempos de respuesta o disponibilidad
   mínima exigida.

4. Aplica las reglas de **umbral de alerta de precio**:
   - Si el precio se desvía más de
     `desviacion_maxima_vs_promedio_pct` respecto al promedio de las
     propuestas → marcar `ALERTA: desviación de precio`.
   - Si el precio está por debajo de
     `precio_anormalmente_bajo_pct` del presupuesto referencial →
     marcar `ALERTA: posible oferta anormalmente baja`.
   - Si el precio supera el presupuesto referencial en más de
     `precio_sobre_presupuesto_pct` → marcar `ALERTA: sobre
     presupuesto`.

5. Completa la plantilla `plantillas/comparativo_comercial.xlsx` con
   todas las propuestas evaluadas y guarda el resultado en
   `outputs/comparativo_comercial.xlsx`.

6. Registra la acción en `logs/auditoria.md`.

## Salida esperada
- Comparativo comercial consolidado (archivo xlsx en `outputs/`).
- Tabla resumen: `Proveedor | Puntaje comercial | Alertas de precio | Cumplimiento SLA`.
- Insumo para el ranking ponderado (`04_ranking.md`).
