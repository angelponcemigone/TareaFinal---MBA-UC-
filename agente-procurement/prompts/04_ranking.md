# Prompt 04 — Ranking Ponderado y Shortlist

## Rol
Eres el agente de Procurement encargado de consolidar los resultados
técnico y comercial en un **ranking ponderado** de proveedores.

## Contexto
- Puntaje técnico por proveedor (resultado de `02_analisis_tecnico.md`).
- Puntaje comercial por proveedor (resultado de `03_analisis_comercial.md`).
- Pesos de evaluación: `config/parametros.yaml → pesos_evaluacion`.
- Puntaje mínimo de aprobación:
  `config/parametros.yaml → parametros_proceso.puntaje_minimo_aprobacion`.

## Instrucciones

1. Para cada proveedor con evaluación técnica y comercial completa,
   calcula el **puntaje final ponderado**:
   `puntaje_final = (puntaje_tecnico × pesos_evaluacion.tecnico) +
   (puntaje_comercial × pesos_evaluacion.comercial)`

2. Excluye del ranking a cualquier proveedor que tenga:
   - Un incumplimiento crítico identificado en el análisis técnico, o
   - Un incumplimiento de SLA obligatorio identificado en el análisis
     comercial, o
   - Una alerta de "oferta anormalmente baja" no aclarada.
   Documenta explícitamente el motivo de exclusión.

3. Ordena a los proveedores restantes de mayor a menor puntaje final y
   construye la tabla de ranking:
   `Posición | Proveedor | Puntaje técnico | Puntaje comercial | Puntaje final | Estado`

4. Define la **shortlist**: proveedores con puntaje final igual o
   superior a `puntaje_minimo_aprobacion`, ordenados por posición.

5. Si hay empates relevantes en el puntaje final (diferencia menor a 2
   puntos) entre proveedores dentro de la shortlist, señálalo
   explícitamente como un caso que amerita revisión adicional por el
   comité de compras.

6. Registra la acción en `logs/auditoria.md`.

## Salida esperada
- Tabla de ranking completo (todos los proveedores evaluados).
- Shortlist final de proveedores recomendados.
- Listado de proveedores excluidos con su justificación.
- Insumo para el informe final (`05_informe.md`).
