TÍTULO: Informe semanal 01 — Fase 1 (18–24 de octubre de 2026)
AUTOR: Musa
FECHA: Completado con el informe paper generado el 2026-10-30 08:42 UTC (fuente: tradesv3_paper_donchian55_f1.sqlite)
TIPO: revisión
RESPONDE A: Aporte Musa PR #4 (seguimiento de la Fase 1) — estructura fijada ahí

## 0. Primera verificación (la condición de todo lo demás)

- [ ] Vía de acceso a los datos del paper CONFIRMADA o NEGADA: registro de decisiones por par y día + informe con cálculo de referencia. Preguntado a Rael el 2026-10-20 (hilo GoaTTheBot); respuesta pendiente.
  - **Nota de Claude (5 nov):** vía CONFIRMADA por Rael el 4 nov. Rael le pasa a Musa cada semana el informe de `fase1/informe_paper_donchian55.py`.
- Si la vía no existe al cerrar la semana 1, este informe lo dice en la primera línea y el seguimiento se declara sin datos — no se finge control.

## 1. Integridad

- MD5 de la ficha: [PENDIENTE DATO] — ¿sigue siendo el registrado al inicio de la Fase 1 (18-oct 00:20 UTC)?
- Reinicios del bot sin explicación: [PENDIENTE DATO]
  - **Nota de Claude (5 nov):** 1 paro sin aviso el 20 oct a las 18:58 UTC (última escritura del log); causa sin confirmar. El bot no volvió a arrancar hasta el 27 oct a las 06:49 UTC, ya en la semana 2.
- Datos Gate.io completos en los 6 pares (BTC, ETH, LTC, XRP, BCH, LINK vs USDT), sin velas diarias faltantes: NO — del 21 al 24 oct no hay evaluación de ningún par (el informe plantea: ¿bot parado o sin velas?). Los días 18, 19 y 20 oct sí fueron evaluados.
  - **Nota de Claude (5 nov):** no comprobable en la semana 1. Del 21 al 24 oct no faltan velas: el bot estuvo parado desde el 20 oct a las 18:58 UTC hasta el 27 oct.

## 2. Concordancia bot vs cálculo de referencia

- Discrepancias sin explicar: ninguna en los datos entregados — el informe del periodo 18–27 oct indica 24 de 24 evaluaciones coincidentes con la referencia. (El desglose solo de la semana 1 no viene separado en la fuente.)
- Toda discrepancia se escala a Rael el mismo día, no espera al informe.

## 3. Riesgo observado

- Riesgo abierto total vs tope del 2% del capital: 0% — posiciones abiertas: 0; resultado no realizado: +0,00 USDT.
- Drawdown desde el pico: 0% — saldo paper 1.000,00 USDT (+0,00%), sin posiciones abiertas. Referencias: kill switch 10%; banda de aviso Monte Carlo P95 6,7% (medida en la compuerta 0→1; es referencia de backtest trasplantada, marcada SUPUESTO como umbral de aviso en el aporte PR #4).

## 4. Exposición por sub-cartera (solo observación; la ficha no se toca)

- conservador 55% (BTC): 0% comprometido (0 posiciones)
- cripto_consolidado 30% (ETH, LTC, XRP, BCH, LINK): 0% comprometido (0 posiciones)
- alto_riesgo 15%: sigue vacía — 0 posiciones
- Vigilancia específica: el ensayo previo que llegó a 122,9% de un bloque (problema abierto d del memorándum 2026-10-19).

## 5. Actividad

- Operaciones abiertas/cerradas en la semana y acumulado: 0 abiertas, 0 cerradas. Entradas: 0. Salidas: 0. Órdenes canceladas: 0. Señales 20+55: 0 en los días evaluados (18, 19 y 20 oct); días 21–24 sin evaluación.
- Referencia orientativa: ~18 operaciones/año según el memorándum; con 2–3 operaciones en 6 semanas, la Fase 1 valida el bot, no el edge.

## 6. Incidentes

- Días seguidos sin incidentes críticos al cierre de la semana 1: 0 de 7 (la exigencia de 14 días seguidos aplica al final de la fase, antes del paso a Fase 2 el 29-nov).
- Total de incidentes críticos de la semana 1: [PENDIENTE DATO] — el informe entrega 69 incidentes para el periodo 18–27 oct, no el desglose de la semana 1.
- Detalle (solo 18–24 oct):
  - 18 oct: el bot no dio señales de vida 25 min (03:46 a 04:11 UTC) y 82 min (05:55 a 07:17 UTC).
  - 20 oct: errores repetidos "Could not load markets" (freqtrade.exchange.exchange) entre las 18:36 y las 18:40 UTC; el bot no dio señales de vida 36 min (09:34 a 10:10 UTC) y 505 min (10:10 a 18:36 UTC).
  - 21, 22, 23 y 24 oct: no hay evaluación de ningún par (¿bot parado o sin velas?).
    - **Nota de Claude (5 nov):** bot parado (ver la nota de la sección 1).

## 7. Estado de los aportes (tabla viva)

| PR | Autor | Tema | Veredicto de Claude | Siguiente paso | Dueño |
|---|---|---|---|---|---|
| #3 | ChatGPT | Selección, deterioro y costes de Donchian 55 | Emitido | Mergeado (21-oct) | Claude / Rael |
| #4 | Musa | Seguimiento Fase 1, costumbres GitHub, visión | Emitido | Mergeado (22-oct) | Claude / Rael |
| #5 | Meta.ai | Pulso de redes + hipótesis H1 de sentimiento | Emitido | Mergeado (21-oct) | Claude / Rael |
| #6 | Perplexity | Evidencia Donchian, costes Kraken y liquidez | Emitido | Mergeado (21-oct) | Claude / Rael |

## Escalación inmediata a Rael (no espera al informe)

- Discrepancia bot vs referencia sin explicación en 24 h
- MD5 distinto del registrado o reinicio sin causa clara
- Hueco de datos de más de una vela diaria en cualquier par
- Drawdown que supere el P95 de Monte Carlo (6,7%)
- Cualquier incidente crítico (rompe la racha de 14 días)
