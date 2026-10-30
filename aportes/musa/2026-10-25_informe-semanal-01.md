TÍTULO: Informe semanal 01 — Fase 1 (18–25 de octubre de 2026)
AUTOR: Musa
FECHA: [borrador preparado 2026-10-20; se cierra el 2026-10-25]
TIPO: revisión
RESPONDE A: Aporte Musa PR #4 (seguimiento de la Fase 1) — estructura fijada ahí

> BORRADOR LOCAL — todavía no subido al repo. El PR #4 sigue esperando el veredicto de Claude y el merge de Rael; este informe usa su estructura como propuesta, no como formato ya adoptado. No toca la ficha congelada.

## 0. Primera verificación (la condición de todo lo demás)

- [ ] Vía de acceso a los datos del paper CONFIRMADA o NEGADA: registro de decisiones por par y día + informe con cálculo de referencia. Preguntado a Rael el 2026-10-20 (hilo GoaTTheBot); respuesta pendiente.
- Si la vía no existe al cerrar la semana 1, este informe lo dice en la primera línea y el seguimiento se declara sin datos — no se finge control.

## 1. Integridad

- MD5 de la ficha: [PENDIENTE DATO] — ¿sigue siendo el registrado al inicio de la Fase 1 (18-oct 00:20 UTC)?
- Reinicios del bot sin explicación: [PENDIENTE DATO]
- Datos Gate.io completos en los 6 pares (BTC, ETH, LTC, XRP, BCH, LINK vs USDT), sin velas diarias faltantes: [PENDIENTE DATO]

## 2. Concordancia bot vs cálculo de referencia

- Discrepancias sin explicar: [PENDIENTE DATO] — objetivo: cero.
- Toda discrepancia se escala a Rael el mismo día, no espera al informe.

## 3. Riesgo observado

- Riesgo abierto total vs tope del 2% del capital: [PENDIENTE DATO]
- Drawdown desde el pico: [PENDIENTE DATO] — referencias: kill switch 10%; banda de aviso Monte Carlo P95 6,7% (medida en la compuerta 0→1; es referencia de backtest trasplantada, marcada SUPUESTO como umbral de aviso en el aporte PR #4).

## 4. Exposición por sub-cartera (solo observación; la ficha no se toca)

- conservador 55% (BTC): [PENDIENTE DATO] % comprometido
- cripto_consolidado 30% (ETH, LTC, XRP, BCH, LINK): [PENDIENTE DATO]
- alto_riesgo 15%: vacía al inicio de la fase — ¿sigue vacía? [PENDIENTE DATO]
- Vigilancia específica: el ensayo previo que llegó a 122,9% de un bloque (problema abierto d del memorándum 2026-10-19).

## 5. Actividad

- Operaciones abiertas/cerradas en la semana y acumulado: [PENDIENTE DATO]
- Referencia orientativa: ~18 operaciones/año según el memorándum; con 2–3 operaciones en 6 semanas, la Fase 1 valida el bot, no el edge.

## 6. Incidentes

- Días seguidos sin incidentes críticos al cierre de la semana 1: [PENDIENTE DATO] de 7 (la exigencia de 14 días seguidos aplica al final de la fase, antes del paso a Fase 2 el 29-nov).

## 7. Estado de los aportes (tabla viva)

| PR | Autor | Tema | Veredicto de Claude | Siguiente paso | Dueño |
|---|---|---|---|---|---|
| #3 | ChatGPT | Selección, deterioro y costes de Donchian 55 | Pendiente | Veredicto → merge | Claude / Rael |
| #4 | Musa | Seguimiento Fase 1, costumbres GitHub, visión | Pendiente | Veredicto → merge | Claude / Rael |
| #5 | Meta.ai | Pulso de redes + hipótesis H1 de sentimiento | Pendiente | Veredicto → merge | Claude / Rael |
| — | Perplexity | Aporte aún no aparece en el repo (verificado 2026-10-20) | — | Aviso redactado, lo envía Rael | Rael |

## Escalación inmediata a Rael (no espera al informe)

- Discrepancia bot vs referencia sin explicación en 24 h
- MD5 distinto del registrado o reinicio sin causa clara
- Hueco de datos de más de una vela diaria en cualquier par
- Drawdown que supere el P95 de Monte Carlo (6,7%)
- Cualquier incidente crítico (rompe la racha de 14 días)
