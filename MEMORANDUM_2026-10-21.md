# Memorándum · 21 oct 2026

```text
MEMORÁNDUM — GoaTTheBot: estado real, aportes entregados y lo que sigue

De: Rael (dueño del proyecto)
Para: Claude (CTO) · ChatGPT · Perplexity · Musa · Meta.ai
Fecha: 21 de octubre de 2026
Asunto: Fase 1 en marcha; aportes completos — tres mergeados, el de Musa en espera

1. Estado real del proyecto (19–21 de octubre)
- Compuerta 0→1 PASADA el 15-oct: Donchian 55 diaria, 161 operaciones 2018–2026, profit factor 2,36, 6 de 9 años positivos, drawdown P95 de Monte Carlo 6,7%, sin lookahead.
- Fase 1 (paper trading) corre desde el 18-oct a las 00:20 UTC: 1.000 USDT simulados, datos públicos de Gate.io, pares BTC/ETH/LTC/XRP/BCH/LINK vs USDT, sub-carteras 55/30/15 (alto_riesgo vacía). Día 42: 29 de noviembre.
- La ficha está CONGELADA por MD5: cualquier cambio reinicia el reloj de 6 semanas. Nada de la Fase 1 se toca mientras dure.
- Pase a Fase 2 (preparada en Kraken, 1.000 USD reales, confirmación humana por operación) exige: 6 semanas completas, 14 días seguidos sin incidentes críticos al final, cero discrepancias sin explicar bot vs. cálculo de referencia, drawdown dentro del rango de Monte Carlo, y el sí explícito de Rael.
- Riesgos abiertos, sin maquillar: el edge se adelgazó desde 2022 (~12,7 USDT por operación desde 2022 vs. 47 en 2018–2021, según el recálculo de ChatGPT; el periodo entero da ~27,8; cifras en revisión hasta reproducirlas en la laptop; backtest dic 2024–oct 2026 con profit factor 0,86); con ~18 operaciones/año, la Fase 1 valida el bot, no el edge; Kraken cobra 0,40% u 0,80% por lado en Fase 2 frente al 0,25% supuesto en el backtest; el reparto 55/30/15 limita cada operación, no el total por bloque (un ensayo llegó al 122,9% de un bloque).

2. Aportes de la convocatoria — tablero al 21-oct
- PR #3 — ChatGPT: selección, deterioro y costes de Donchian 55. MERGEADO el 21-oct.
- PR #4 — Musa: seguimiento de la Fase 1 hasta el 29-nov, costumbres del equipo en GitHub y visión. ABIERTO — veredicto de Claude ya dado (Adoptar, 20-oct); falta el merge. Es el único pendiente.
- PR #5 — Meta.ai: pulso de redes cripto (sep–oct 2026) e hipótesis medible H1 (las rupturas Donchian 55 con sentimiento extremo rinden peor que con sentimiento neutro; se probaría offline sobre las 161 operaciones históricas, sin tocar la Fase 1). Subido por Musa TAL CUAL, verificado byte por byte (16.227 bytes), porque Meta.ai no tiene acceso a GitHub. MERGEADO el 21-oct.
- PR #6 — Perplexity: evidencia Donchian, costes Kraken y liquidez. Perplexity tuvo fallos técnicos para subirlo; Rael entregó el texto y Claude lo subió sin editar. MERGEADO el 21-oct.
- Los cuatro aportes están dentro. Solo el PR #4 espera su turno.

3. Corrección de roles (queda asentada)
La tabla del 2-oct aún lista a Grok en revisión adversarial. Por decisión de Rael del 8-oct, Grok está fuera; Meta AI lo sustituye, y el revisor adversarial es ChatGPT o una segunda llamada a Claude. Ningún miembro trabaja con la tabla vieja.

4. Lo que sigue, en orden
1. El merge del PR #4 (el veredicto de Claude, Adoptar, ya está dado desde el 20-oct), como se hizo con los otros tres.
2. Seguimiento semanal de la Fase 1 por Musa (informe de una página: integridad MD5, concordancia bot vs. referencia, riesgo y drawdown vs. banda de Monte Carlo, exposición por bloque, contador de días sin incidentes). Punto débil declarado: el informe depende de que el registro de decisiones del paper y el informe de referencia le lleguen a Musa por alguna vía (exportación, archivo o capturas). Esa vía aún no está definida.

5. Decisiones que quedan en manos de Rael
a) Distribuir este memorándum tal cual o ajustarlo antes.
b) Definir la vía de datos de la Fase 1 para el seguimiento semanal de Musa antes del cierre de la semana 1 (sábado 25-oct).
c) (Cuando quiera) Elegir 1 de las 3 direcciones de avatar de GoaTTheBot.
```

Nota de edición (22 oct 2026, Claude, a pedido de Rael): el texto estuvo por error en la descripción del PR #4. Al pasarlo aquí se rellenó la fecha, se corrigió la cifra de 47 USDT por operación (corresponde a 2018–2021, no al periodo entero, y sigue en revisión) y se indicó que el veredicto del PR #4 ya estaba dado. El resto es el texto original.
