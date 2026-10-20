TÍTULO: Pulso de redes cripto (sep–oct 2026) e hipótesis medible: ¿el sentimiento extremo empeora las rupturas Donchian 55?
AUTOR: Meta.ai
FECHA: 2026-10-20
TIPO: investigación

## 1. Resumen en 3 líneas
Pulso de redes del último mes sobre BTC, ETH, LTC, XRP, BCH y LINK: dominan el debate cíclico de BTC ("Octobull vs Octobear"), la tensión geopolítica (EE. UU.–Irán, petróleo >100 USD) como marco de volatilidad, y una oleada de promesas de bots de trading con IA sin evidencia verificable. Propongo como hipótesis medible que las rupturas Donchian 55 ocurridas con sentimiento de redes extremo (euforia o pánico) tienen peor resultado por operación que las rupturas con sentimiento neutro, con criterios de éxito y fracaso fijados antes de medir nada. Todo lo no medido con datos reproducibles va marcado como SUPUESTO.

## 2. Propuesta

### 2a. Pulso de redes (contexto, no señal)

**Metodología del pulso (limitada y honesta):** muestreo de publicaciones públicas en Instagram/Facebook/Threads entre el 20-sep-2026 y el 20-oct-2026 mediante búsqueda semántica, ordenadas por engagement y recencia. No es un censo exhaustivo de redes; es una muestra con sesgo hacia contenido de alto engagement. Lo que sigue describe lo observado en esa muestra, no el estado medido de "todas las redes".

**Temas dominantes observados:**

1. **BTC domina la conversación; las otras 5 monedas casi no aparecen.** En la muestra, BTC concentra la gran mayoría de publicaciones. ETH aparece de forma secundaria (gráficos de portadas de análisis geopolítico, p. ej. una publicación del 13-oct-2026 que mostraba BTC ∼83.300 USD y ETH ∼2.564 USD). LTC, XRP, BCH y LINK no tuvieron presencia significativa en la muestra del último mes: el pulso de redes, tal como lo puedo medir, es esencialmente un pulso de BTC con menciones ocasionales a ETH.
2. **Debate cíclico estacional: "Octobull vs Octobear".** Una publicación educativa del 30-sep-2026 presentaba la tabla histórica de retornos mensuales de BTC (octubre con media +18,49% desde 2013) y dividía a la audiencia entre quienes esperan un octubre verde por historia y quienes advierten de sobrecompra. Es el marco narrativo dominante del mes: la estacionalidad como argumento de posicionamiento.
3. **Predicciones de ciclo con fechas concretas.** Un creador con ∼3M de seguidores publicó el 29-sep-2026 un análisis proyectando un giro bajista alrededor del 5-oct-2026 basado en un patrón de 364 días bajistas / 1.064 alcistas repetido desde 2017. Tono instructivo y seguro, con llamada a comentar para recibir "el análisis detallado" (cebo de engagement). Este tipo de contenido calendario-fijo genera ansiedad medible en comentarios.
4. **Geopolítica como marco de volatilidad.** La escalada EE. UU.–Irán, con el Brent por encima de 100 USD en octubre, aparece como explicación de la volatilidad y la sensibilidad al riesgo en cripto. Una portada de análisis del 13-oct-2026 titulaba literalmente "Guerra, cripto y mercados globales". SUPUESTO: que este marco narrativo mueva precios de forma causal no está medido; solo está medido que domina el encuadre.
5. **Caída del 8 de octubre y liquidaciones.** Una publicación del 8-oct-2026 reportó BTC por debajo de 81.000 USD con más de 480M USD en liquidaciones apalancadas, citando salidas de ETFs, rendimientos del Tesoro, dólar fuerte y tensiones geopolíticas. Los comentarios muestran el rango 80K–84K como zona de batalla técnica (media de 50 días como soporte a defender; objetivo bajista ∼74.000 si se pierde, según un analista el 16-oct-2026).
6. **Acumulación corporativa como narrativa alcista estructural.** El 18-oct-2026 se difundió una captura de una publicación de Michael Saylor ("We found room for more orange") con el dato de 848.250 BTC en reserva (∼69.450M USD, precio medio 75.444 USD). Los comentarios se dividen entre defensores de la estrategia de tesorería y acusaciones de esquema pump/dump, más una densa capa de spam (enlaces de WhatsApp, "mentores", tokens especulativos). Señal de ruido: en publicaciones financieras de alto alcance, una fracción grande de la "conversación" es spam promocional, no sentimiento genuino.
7. **Lo que cambió en el último mes (dentro de la muestra):** de un septiembre dominado por el debate estacional ("¿octubre verde o rojo?") se pasó en octubre a un encuadre de **riesgo geopolítico + niveles técnicos defensivos** (50-day MA, zona 80K–82,5K como "order block"). El tono agregado se movió de especulación estacional a ansiedad defensiva. SUPUESTO: este desplazamiento de tono es una lectura cualitativa de la muestra, no una serie temporal cuantificada.

### 2b. Hipótesis medible (el aporte central)

**Hipótesis H1:** En la estrategia Donchian 55 diaria, las operaciones cuya señal de entrada coincide con **sentimiento de redes extremo** (euforia o pánico en la ventana previa a la señal) tienen un resultado medio por operación (neto de costes) **peor** que las operaciones con sentimiento neutro.

**Definiciones operativas (fijadas antes de medir):**
- **Ventana de sentimiento:** 7 días naturales previos al cierre que genera la señal (incluido ese día), por par (p. ej. solo menciones de BTC para señales de BTC; para pares sin volumen de menciones suficiente —LTC, XRP, BCH, LINK— se usa el sentimiento agregado del mercado cripto; esta decisión queda registrada antes del cálculo).
- **Métrica de sentimiento:** puntuación diaria de un clasificador de sentimiento aplicado a publicaciones públicas muestreadas con protocolo fijo (misma query, mismo ranking, mismo N por día). Definir "extremo" como: puntuación en el decil superior (euforia) o inferior (pánico) de la distribución histórica de esa misma métrica en el periodo 2018–2026. El protocolo de muestreo y el clasificador se congelan antes de ver resultados.
- **Unidad de análisis:** cada operación histórica de la Donchian 55 (las 161 del backtest 2018–2026 ya existentes sirven como base; no se genera ningún backtest nuevo para este aporte).
- **Métrica de resultado:** retorno por operación neto de los costes ya definidos en la ficha (0,25% por lado en la especificación vigente).

**Criterio de éxito (fijado antes):** la diferencia de medias (extremas menos neutras) es negativa y estadísticamente significativa al 5% (test de permutación, 10.000 réplicas), Y el tamaño del efecto supera el 50% del coste de ida y vuelta (0,20% con 0,25% por lado), es decir, es económicamente relevante además de estadística.

**Criterio de fracaso (fijado antes):** p ≥ 0,05, o diferencia menor a 0,20% en valor absoluto, o la diferencia cambia de signo al excluir cualquier año individual (falta de robustez temporal). Cualquiera de las tres cosas invalida H1.

**Variante H2 (si H1 falla pero hay señal parcial):** solo el extremo de **euforia** empeora las rupturas alcistas (falsas rupturas por FOMO), mientras el pánico no aporta nada. Mismo criterio estadístico, pre-registrado como análisis secundario, no como rescate post-hoc.

**Nota de encaje con la ficha congelada:** esta hipótesis se prueba **offline** sobre el histórico ya existente. No toca nada de la Fase 1, no cambia entradas/salidas/stops, no filtra operaciones en vivo. Si H1 se confirmara, su uso futuro (p. ej. como filtro o como ajuste de tamaño) sería una propuesta separada para después de la Fase 1, con el reloj reiniciado según las reglas.

## 3. Por qué debería funcionar: la lógica económica y quién está del otro lado

La Donchian 55 es una estrategia de ruptura de tendencia: compra cuando el precio confirma fortaleza (cierre sobre máximos de 20 y 55 días). Su riesgo conocido es la **falsa ruptura**: entrar justo cuando el impulso se agota.

La lógica económica de H1: el sentimiento extremo de redes es un proxy observable del **posicionamiento minorista tardío**. Quien está del otro lado de una ruptura eufórica no es un informado con ventaja, sino el flujo minorista que llega tarde por FOMO más la toma de beneficios de quienes compraron antes y usan esa liquidez para salir. En euforia extrema, la ruptura atrae compradores sin convicción (stop ajustados, manos débiles) cuya capitulación posterior acelera la llegada al stop. En pánico extremo, la dinámica es menos clara para una estrategia solo-largos: el pánico puede generar rupturas "baratas" que sí funcionan, por eso H2 separa ambos extremos.

SUPUESTO: que el sentimiento de redes mida realmente posicionamiento minorista y no solo ruido/spam (la muestra muestra mucho spam promocional, lo que contamina la métrica). SUPUESTO: que la relación sentimiento-ruptura observada en 2018–2026 sea estable hacia adelante, cuando el propio memorándum documenta que el edge se ha adelgazado desde 2022.

## 4. Cómo se mide: datos, pasos, con criterio de éxito y fracaso fijados antes

**Datos:**
- Operaciones: el registro existente de las 161 operaciones 2018–2026 de la Donchian 55 (ya verificado, sin lookahead). Ningún backtest nuevo.
- Sentimiento: archivo público y reproducible de publicaciones (IDs/URLs, fecha, texto, métrica de engagement), con el protocolo de muestreo documentado: queries fijas por par, N publicaciones por día, ventana 2018–2026. Donde no haya cobertura histórica suficiente en redes (pre-2020 para altcoins), se registra el hueco en vez de imputarlo en silencio.
- Clasificador de sentimiento: modelo o lexicón fijado y versionado antes del análisis; su validación (precisión sobre muestra etiquetada manualmente, p. ej. 500 publicaciones) se reporta antes de cruzar con operaciones.

**Pasos:**
1. Congelar protocolo de sentimiento (queries, clasificador, definición de deciles) y registrarlo con hash/fecha. Criterio de éxito/fracaso ya fijado (ver 2b).
2. Etiquetar cada operación histórica como "sentimiento extremo" o "neutro" según la ventana de 7 días previa. Una sola variable: el flag de sentimiento.
3. Test de permutación sobre la diferencia de medias netas por operación. Reportar también por subperiodos (2018–2021 vs 2022–2026) dado el adelgazamiento del edge documentado.
4. Chequeo de robustez: excluir un año cada vez; si el signo cambia, H1 fracasa aunque el p-valor agregado sea <0,05.
5. Publicar el dataset de sentimiento y el código del análisis para reproducción. Sin esto, el resultado no cuenta.

**Lo que NO se hace:** no se optimiza el umbral de "extremo" (deciles fijados a priori, no barrido de percentiles); no se prueba H2 como rescate si H1 falla salvo que se pre-registró como secundario; no se toca la Fase 1.

## 5. Supuestos y lo que no sabes

- SUPUESTO: el sentimiento extraído de redes públicas representa a participantes marginales del mercado y no puro ruido/spam. La muestra del último mes muestra contaminación alta por spam (enlaces de WhatsApp, "mentores", tokens), lo que puede inutilizar la métrica.
- SUPUESTO: cobertura histórica suficiente de sentimiento por par desde 2018. Para LTC/XRP/BCH/LINK es dudoso; el protocolo debe definir el fallback (sentimiento agregado) antes de medir.
- SUPUESTO: estabilidad temporal de la relación, en un contexto donde el edge de la estrategia se ha adelgazado desde 2022 (12,7 USDT vs 47 por operación; profit factor 0,86 en dic 2024–oct 2026).
- No sé: qué clasificador funcionará mejor en jerga cripto multilingüe (la muestra incluye inglés, español, indonesio, persa); qué latencia tiene el sentimiento respecto a la señal; si el efecto, de existir, sobrevive a los costes taker de Kraken en Fase 2 (0,40%/0,80% por lado), que ya de por sí comprimen el edge.
- No presento ningún resultado numérico propio: no he corrido ningún backtest ni medición. Todo lo cuantitativo anterior son umbrales propuestos, no resultados.

## 6. Riesgos: qué podría salir mal

1. **La métrica es ruido.** El spam y el engagement-bait dominan las publicaciones de alto alcance; el "sentimiento" medido podría no correlacionar con nada real. El criterio de fracaso está diseñado para detectar exactamente esto.
2. **P-hacking accidental.** Probar euforia/pánico/ventanas/métricas hasta encontrar algo. Mitigación: una variable, umbrales pre-fijados, pre-registro.
3. **Falsa confianza por confirmación.** Si H1 "funciona" en el histórico, la tentación será usarla en vivo. Pero con ∼18 operaciones/año, la muestra de "extremas" será minúscula (quizá 3–5 operaciones en 6 semanas de paper): cualquier filtro basado en esto tardaría años en validarse. Debe quedar como investigación, no como cambio de estrategia, hasta completar un ciclo de validación propio.
4. **Coste de oportunidad.** El tiempo de construir el dataset de sentimiento 2018–2026 es significativo y podría rendir más invertido en el problema documentado como crítico: los costes taker de Kraken en Fase 2.
5. **Riesgo de interpretación pública.** Si el proyecto cita "sentimiento de redes" sin los matices, puede sonar a las promesas sin evidencia que criticamos en 2c. Cualquier comunicación debe incluir los criterios de fracaso.

### 2c. Promesas sobre bots de trading con IA que circulan sin evidencia (para no repetirlas)

Observadas en la muestra del último mes, todas con el mismo patrón (cifras espectaculares + captación por comentario/DM + cero auditoría):

1. **"10 USD → 560 USD en 10 horas"** (video en persa, 6-oct-2026): bot de "IA" que analiza todos los exchanges, gestiona el riesgo solo y ofrece prueba gratis de 15 días. Los comentarios lo llaman estafa de forma mayoritaria.
2. **"6 bots de IA convirtieron 89 USD en 55.698 USD mientras dormía"** (múltiples variantes, 7-oct y 16-oct-2026): "mesa virtual" de seis bots (Jefe, Scout, News, Sentimiento, Charts, Escéptico). Misma mecánica: comentar una palabra clave para recibir la "guía" por DM. Sin track record auditable, sin comisiones declaradas, sin drawdown declarado.
3. **"68% de win rate" como argumento de rentabilidad** (1-oct-2026): el win rate sin el ratio ganancia/pérdida ni los costes no dice nada; una estrategia con 68% de aciertos y mala asimetría pierde dinero. Presentarlo como prueba de rentabilidad es la falacia más repetida.
4. **"La IA opera sin emociones, por eso gana"**: la ausencia de emoción no es un edge; un sistema sin edge ejecutado sin emociones pierde dinero de forma disciplinada. Ninguna de estas publicaciones muestra backtest con costes, slippage, ni out-of-sample.
5. **Testimonios con capturas de pantalla** ("87 USD → 8.391 USD en 18 horas"): sin historial completo, sin operaciones perdedoras visibles, sin forma de distinguir una cuenta demo de una real.

**Regla práctica que propongo para el proyecto:** cualquier afirmación externa sobre bots/IA que no incluya (a) número de operaciones, (b) periodo, (c) costes aplicados y (d) fuera de muestra, se clasifica automáticamente como ruido promocional y no se discute como evidencia. Es el mismo estándar que el proyecto ya se aplica a sí mismo.

## 7. Encaje con las reglas de la sección 7

- **Solo spot, solo largos:** este aporte no propone operar nada distinto; es investigación offline sobre el histórico existente.
- **Ficha de Fase 1 intacta:** no se modifica ningún archivo operativo, parámetro, stop ni filtro en vivo. H1 se prueba sobre datos históricos ya registrados.
- **Nada hacia dinero real sin el sí de Rael:** no se propone ningún cambio con efecto en ejecución. Si H1 se confirmara, su eventual uso sería una propuesta futura separada, con reinicio del reloj según las reglas.
- **Sin claves ni secretos:** este texto no contiene ni pide ninguna credencial, token ni acceso.
- **SUPUESTO marcado:** todo lo no medido con datos reproducibles va etiquetado como SUPUESTO (secciones 2a, 3 y 5).
- **Una variable por experimento:** el único grado de libertad es el flag binario de sentimiento extremo; umbral (deciles), ventana (7 días) y test (permutación, 10.000 réplicas) quedan fijados antes.
- **Propuesta, no instrucción:** no contiene instrucciones para Claude ni para ninguna otra IA; no asume accesos, conexiones ni herramientas no confirmadas. La verificación queda en manos de Claude y la decisión en manos de Rael.
