TÍTULO: Donchian en cripto: evidencia, costes ejecutables y volatilidad líquida
AUTOR: Perplexity
FECHA: 2026-10-20
TIPO: investigación / revisión
RESPONDE A: CONVOCATORIA_2026-10-19.md, apartado Perplexity

## 1. Resumen

La literatura relacionada no valida la configuración exacta Donchian 55 spot y solo largos, ni demuestra una desaparición general del efecto desde 2022.
La consulta oficial previa de Kraken muestra 0,40% maker y 0,80% taker en el tramo inicial; requiere confirmar categoría y par antes de cualquier uso real.
Se propone investigar costes y liquidez antes de ampliar activos, sin modificar la Fase 1 ni dar señales de compra o venta.

## 2. Propuesta

Este aporte propone investigación separada del bot operativo. No cambia entrada, salida, stop, tamaño ni asignaciones. No propone llenar alto_riesgo inmediatamente.

### Evidencia académica y sus límites

- Hudson y Urquhart, Technical trading and cryptocurrencies, Annals of Operations Research: publicación en línea 30-08-2019, volumen de 2021. Examina reglas técnicas, incluidas rupturas, en criptomonedas y aplica controles de pruebas múltiples. También informa ausencia de predictibilidad de BTC fuera de muestra. Es evidencia relacionada, no validación de Donchian 55 ni de spot solo largos. Fuente: https://link.springer.com/article/10.1007/s10479-019-03357-1
- Grobys y Sapkota, Cryptocurrencies and momentum, Economics Letters, 2019. Estudia 143 criptomonedas durante 2014–2018 y cuestiona la solidez del momentum. No equivale a una prueba de Donchian. Fuente: https://osuva.uwasa.fi/bitstreams/ffee5cb1-92a8-443e-a117-cbaacd8a1028/download
- Moskowitz, Ooi y Pedersen, Time series momentum, Journal of Financial Economics, 2012. Evidencia en 58 instrumentos líquidos de futuros y forwards; datos originales de enero de 1985 a diciembre de 2009. Comparación para la familia de seguimiento de tendencia, no para cripto spot ni para Donchian exacto. Se cita exclusivamente como comparación bibliográfica, no como propuesta de derivados. Fuente y datos originales: https://www.aqr.com/Insights/Datasets/Time-Series-Momentum-Original-Paper-Data
- Gbadebo, Momentum Trading in Cryptocurrencies: A Comparative Study of Time-Series and Cross-Sectional Strategies, 2026. El texto examinado estudia ocho criptomonedas entre 01-01-2020 y 31-10-2025 mediante medias exponenciales y normalización por volatilidad. Informa momentum favorable, pero excluye costes y contempla cortos; no valida rentabilidad neta Donchian spot. Presenta inconsistencias internas en normalización y pesos que aconsejan no trasladar sus cifras sin revisión. Fuente: https://www.journals.vu.lt/BATP/en/article/download/44540/42590/138419

No encontré entre las fuentes examinadas una prueba directa y comparable de ruptura estructural de Donchian diario spot a partir de 2022. Los resultados internos comunicados por el proyecto son pertinentes, pero no los he reproducido. No permiten atribuir causalidad a institucionalización, eficiencia, costes o régimen.

### Blogs y divulgación, no evidencia de rentabilidad

- TrendSpider, Donchian Channel Trading Strategies, ficha recuperada fechada 12-04-2023: explicación educativa, no una validación reproducible de esta configuración. https://trendspider.com/learning-center/donchian-channel-trading-strategies/
- AvaTrade, Donchian Channel Indicator – Trading Strategies, ficha recuperada fechada 03-09-2024: educación de un intermediario, no estudio independiente del bot. https://www.avatrade.com/education/technical-analysis-indicators-strategies/donchian-channel-trading-strategies

Las fechas de ficha no certifican el historial de modificaciones. No se propone reintroducir los filtros de confluencia sugeridos por contenidos educativos.

### Comisiones Kraken

Página oficial: https://www.kraken.com/features/fee-schedule
Fecha de consulta de la investigación previa: 2026-10-20. Página dinámica, sin copia archivada adjunta; no certifica retrospectivamente el 18 de octubre ni constituye comprobación de una cuenta concreta.

La tabla general Spot Crypto recuperada muestra estos tramos por volumen spot móvil de 30 días, en USD:

| Volumen desde | Maker | Taker |
|---:|---:|---:|
| 0 | 0,40% | 0,80% |
| 2.500 | 0,30% | 0,60% |
| 10.000 | 0,22% | 0,38% |
| 25.000 | 0,20% | 0,35% |
| 50.000 | 0,15% | 0,30% |
| 100.000 | 0,12% | 0,25% |
| 250.000 | 0,10% | 0,22% |
| 500.000 | 0,08% | 0,20% |
| 1.000.000 | 0,06% | 0,18% |
| 2.500.000 | 0,04% | 0,15% |
| 5.000.000 | 0,02% | 0,12% |
| 10.000.000 | 0,00% | 0,10% |
| 50.000.000 | 0,00% | 0,09% |
| 100.000.000 | 0,00% | 0,08% |
| 250.000.000 | 0,00% | 0,07% |
| 400.000.000 | 0,00% | 0,06% |
| 500.000.000 | 0,00% | 0,05% |

Fuente de todas las cifras de la tabla: página oficial indicada. SUPUESTO de aplicación: cuenta con 1.000 USD sin volumen previo ni condición que mejore categoría. El saldo por sí solo no determina la comisión; la página también contempla activos en plataforma. Hay excepciones por producto y por determinados pares que no he verificado individualmente.

Con nominales iguales, dos ejecuciones taker al 0,80% suman aproximadamente 1,60% antes de spread y deslizamiento: derivación aritmética, no medición del bot. Una orden limitada no garantiza maker si consume liquidez. La página indica que una stablecoin solo como moneda cotizada no traslada automáticamente el par a la tabla de stablecoins. No se propone aumentar rotación para buscar descuentos ni cambiar a maker sin otro experimento.

### Volatilidad sin baja liquidez

No encontré un umbral académico universal aplicable al tamaño del proyecto. Los criterios pertinentes son spread, profundidad, impacto del tamaño previsto, fiabilidad del volumen y comportamiento durante estrés; la selección por volatilidad vendría después.

- Order Book Liquidity on Crypto Exchanges, 26-02-2025: evidencia sobre dimensiones del libro y medidas de liquidez. https://www.mdpi.com/1911-8074/18/3/124
- How to measure the liquidity of cryptocurrency markets?, 2020: estudio específico de medición. No recuperé su texto completo; no le atribuyo un ranking de estimadores. https://www.sciencedirect.com/science/article/pii/S0378426620303022
- Cong, Li, Tang y Yang, Crypto Wash Trading, versión SSRN de julio de 2023: muestra de 29 exchanges y estimación media superior al 70% del volumen declarado como wash trading en los exchanges no regulados de su muestra. No es una estimación particular de Kraken o Gate.io. https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3530220
- Cryptocurrency liquidity and volatility interrelationships during the COVID-19 pandemic, publicación en línea 16-05-2021: interacciones entre volatilidad y liquidez. https://pmc.ncbi.nlm.nih.gov/articles/PMC8856899/

La fuente profesional Kaiko distingue spread y profundidad por mercado, pero no es literatura académica revisada por pares: https://www.kaiko.com/resources/the-crypto-liquidity-concentration-report . La fecha editorial original de ese contenido no quedó establecida en la consulta.

## 3. Por qué debería funcionar

SUPUESTO económico: la reacción gradual a información y los flujos persistentes pueden producir tendencias. La literatura de momentum ofrece explicaciones posibles, no garantías para cualquier ruptura. La comparación principal es el trabajo de Moskowitz, Ooi y Pedersen citado arriba.

SUPUESTO sobre contraparte: un vendedor spot puede rebalancear, tomar beneficios o aportar liquidez; no necesita estar equivocado. El bot necesita que la continuación compense falsas rupturas y costes.

SUPUESTO de selección: filtrar liquidez antes de ordenar volatilidad podría evitar depender de movimientos no ejecutables. No he medido que mejore GOATTHEBOT. Volatilidad no equivale a tendencia ni a rentabilidad esperada.

## 4. Cómo se mide

Todos los umbrales siguientes son SUPUESTOS de diseño propuestos, no hallazgos, parámetros optimizados ni compuertas aprobadas. Experimentos en una copia de investigación, sin tocar Fase 1.

### A. Efecto aislado de comisión

Variable única: comisión por ejecución, 0,25% frente a 0,80%. Mismos datos congelados, versión, estrategia, pares, modelo de ejecución y reglas. Registrar huellas y exportar operaciones, nominales, comisiones y equity. Documentar los cambios de tamaños posteriores inducidos por comisiones.

SUPUESTO de criterio: éxito económico si en el periodo reciente predeclarado el resultado neto y la expectativa neta son positivos y PF > 1 con coste ejecutable. Fracaso si no. Inconcluso si faltan datos o hay discrepancias sin explicar. Reconciliar PF y media si parecen contradictorios: mismas operaciones, definición neta y ponderación. Aprobar no valida por sí solo el edge ni autoriza dinero real.

### B. Debilitamiento temporal

Contraste único: 2018–2021 frente a 2022–última vela diaria completa de los datos congelados. Misma estrategia y costes. Comparar expectativa en unidades de riesgo inicial y P&L monetario. Remuestreo por bloques de calendario preservando dependencia entre pares.

SUPUESTO de criterio: respaldo al debilitamiento si el intervalo de confianza del 95% de la diferencia posterior menos anterior queda completamente bajo cero. Si incluye cero: inconcluso; si queda completamente encima: evidencia contraria bajo este contraste. Como el deterioro reciente ya se conoce, el análisis es retrospectivo y no constituye nueva muestra virgen. El tamaño de bloque y método de intervalo tendrían que fijarse antes de ejecutar; este aporte no aporta código ni resultados.

### C. Universo volátil y líquido

Primera etapa solo de ejecutabilidad, sin medir beneficios. SUPUESTOS de diseño: observación prospectiva de libros durante 30 días, capturas cada minuto y mínimo 99% de capturas válidas por candidato. Evaluar el nominal máximo permitido por las reglas del bloque, cuya definición agregada sigue pendiente según la convocatoria.

SUPUESTO de criterio: percentil 95 del coste de ejecución, sin comisión, no superior al 0,20% por lado para ese tamaño. Fracaso si incumple calidad o coste; ausencia de datos se clasifica no verificable. Antes de correrlo debe fijarse cómo se calculará el coste contra el precio medio y cómo se tratarán libros insuficientes.

Tras superar liquidez, SUPUESTO de selección: cuartil superior de volatilidad, calculada con desviación estándar de retornos logarítmicos de los 60 días anteriores, usando solo datos disponibles en cada fecha. No se recomienda ningún activo. Añadir candidatos y evaluar retorno sería otro experimento, uno a la vez. Alto_riesgo puede permanecer vacía.

## 5. Supuestos y lo que no sabes

No he ejecutado backtests ni inspeccionado el bot operativo. Las cifras internas son información comunicada, no reproducida. Toda hipótesis causal, aplicabilidad al proyecto y umbral propuesto se considera SUPUESTO.

Las cifras bibliográficas y tarifas son datos publicados atribuidos, no mediciones propias; su aplicación es SUPUESTO hasta verificación reproducible. No hay validación directa encontrada de la configuración exacta, ni prueba suficiente de desaparición general desde 2022. No medí libros, impacto o disponibilidad histórica de candidatos. No adjunto copias archivadas de fuentes ni scripts de reproducción; estos límites impiden tratar el aporte como validación concluida.

## 6. Riesgos

Transferir resultados largos/cortos a solo largos; confundir momentum con Donchian; interpretar ruido como ruptura estructural; sesgo de supervivencia; seleccionar volatilidad causada por saltos o manipulación; confiar en volumen declarado; presupuestar maker sin simular no ejecuciones; ignorar deterioro del libro al salir; ampliar activos sin resolver límites agregados de bloques.

Estos son riesgos a investigar, no incidencias nuevas verificadas del bot. También existe riesgo de actualización de tarifas y de extracción incompleta de fuentes web.

## 7. Encaje con las reglas

Solo spot y solo largos en la propuesta. Sin apalancamiento, margen, futuros ni perpetuos; las referencias académicas a derivados son únicamente comparativas. Sin señales de compra o venta. No cambia la ficha, archivos ni reloj de Fase 1. No solicita ni contiene claves. No aplica nada con dinero real. Propuesta para verificación y decisión de Rael, no instrucciones a otra IA. Un contraste o variable principal por experimento, con criterios previos; detalles pendientes deben fijarse antes de ejecutar. No hay backtests propios inventados. No se hace merge.
