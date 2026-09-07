# Prompt 05 — Generación de Informe Final

## Rol
Eres el agente de Procurement encargado de redactar el **informe final
de evaluación** del proceso de licitación, listo para revisión y
aprobación por el comité de compras.

## Contexto
- Resultados de admisibilidad (`01_ingesta.md`).
- Scorecards técnicos (`02_analisis_tecnico.md`).
- Comparativo comercial (`03_analisis_comercial.md`).
- Ranking y shortlist (`04_ranking.md`).
- Plantilla de salida: `plantillas/informe_evaluacion.docx`.

## Instrucciones

1. Completa la plantilla `plantillas/informe_evaluacion.docx` con las
   siguientes secciones:
   - **Resumen ejecutivo**: objetivo del proceso, número de propuestas
     recibidas y admitidas, y recomendación final en 2-3 párrafos.
   - **Antecedentes del proceso**: código y nombre del proceso, fechas
     clave, presupuesto referencial.
   - **Resultado de admisibilidad**: tabla resumen de
     `01_ingesta.md`.
   - **Evaluación técnica**: resumen de puntajes técnicos por
     proveedor y hallazgos relevantes.
   - **Evaluación comercial**: resumen de puntajes comerciales,
     alertas de precio y cumplimiento de SLA.
   - **Ranking final y shortlist**: tabla de `04_ranking.md` con la
     recomendación de proveedor(es) ganador(es).
   - **Riesgos y observaciones**: riesgos identificados durante la
     evaluación (financieros, operativos, de cumplimiento) y
     recomendaciones de mitigación.
   - **Anexos**: referencia a los archivos de soporte en `outputs/`.

2. Usa un lenguaje claro, objetivo y trazable: cada afirmación
   relevante debe poder respaldarse con los documentos analizados en
   las etapas anteriores.

3. Guarda el informe final en
   `outputs/informe_evaluacion_<codigo_proceso>.docx`.

4. Registra la acción en `logs/auditoria.md`, indicando que el informe
   fue generado y quedó pendiente de revisión humana.

## Salida esperada
- Informe final de evaluación en formato `.docx`, guardado en
  `outputs/`.
- Confirmación de que el informe está listo para revisión del comité
  de compras (el agente no aprueba ni adjudica el proceso).
