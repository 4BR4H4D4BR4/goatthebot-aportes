TÍTULO: Donchian 55: evidencia seleccionada, deterioro reciente y dos experimentos de costes
AUTOR: ChatGPT
FECHA: 2026-10-20
TIPO: revisión / investigación / visión
RESPONDE A: CONVOCATORIA_2026-10-19.md, encargo de ChatGPT, puntos 1–4

## 1. Resumen

El PF 2,36 se reproduce como estadístico de dos resultados guardados; no demuestra por sí mismo una ventaja futura libre de selección.
La prioridad propuesta es corregir la trazabilidad, cuantificar la incertidumbre por episodios y evaluar dos cambios aislados: entrada maker y filtro de coste/volatilidad.
Nada de este aporte modifica la Fase 1 ni autoriza operaciones reales; cada experimento puede terminar en fracaso o evidencia insuficiente.

## 2. Propuesta

### 2.1 Revisión adversarial y correcciones de trazabilidad

**COMPROBADO LOCALMENTE, 20/10/2026:** lectura de archivos existentes y recálculo de sus operaciones; no son backtests nuevos ni una auditoría completa de los precios de ejecución.

| Resultado guardado, capital inicial 10.000 USDT por tramo | Operaciones | PF monetario neto | P&L neto | Media neta USDT/op | Episodios por solapamiento |
|---|---:|---:|---:|---:|---:|
| 2018–2021 | 71 | 3,226833 | 3.335,641076 | 46,980860 | 23 (7 positivos) |
| 2022–24/09/2026 | 90 | 1,636082 | 1.142,910652 | 12,699007 | 31 (9 positivos) |
| Concatenación de ambos | 161 | 2,359308 | 4.478,551727 | 27,817091 | 54 (16 positivos) |

Los 47 USDT/op corresponden al tramo antiguo, no al conjunto. Los 54 episodios corresponden a ambos tramos con la definición de solapamiento utilizada aquí, no solo a las 71 operaciones antiguas. Son correcciones documentales propuestas; no revocan la decisión registrada 0→1.

**Límite de interpretación:** cada backtest comenzó con 10.000 USDT. Concatenar sus operaciones reproduce el PF publicado, pero no equivale a una simulación continua con capital, posiciones, bloqueos y máximo de equity arrastrados entre 2021 y 2022. Tampoco prueba el DD continuo ni el P95 de Monte Carlo. El P95 6,7% es MEDIDO APORTADO por la convocatoria; no recalculado en este aporte.

**COMPROBADO EN EL CÓDIGO LOCAL:** ambos canales usan máximos de `high`, ventanas anidadas y `shift(1)`. Con historial completo, `max55 >= max20`; por tanto, `close > max55` ya implica `close > max20`. La entrada 20 Y 55 es una ruptura de 55 días, no dos confirmaciones independientes. En las seis series locales hubo cero diferencias entre ambas expresiones en 19.499 velas-par con ambos canales definidos. La redundancia no elimina el sesgo de elegir 55 mirando resultados.

**MEDIDO APORTADO:** 2022–2026 participó en esa elección. **SUPUESTO pendiente de evidencia de fechas:** 2018–2021 no intervino en elegir universo, horizonte, stop, tamaño ni descartes anteriores. Un periodo anterior puede ser una reserva retrospectiva legítima si se mantuvo oculto; no es validación prospectiva y no queda intacto después de reutilizarlo para nuevas decisiones.

**COMPROBADO LOCALMENTE:** Freqtrade calcula el PF con `profit_abs`, pero la columna de media porcentual usa `profit_ratio`. Un PF monetario mayor que uno puede coexistir con una media porcentual negativa por tamaños diferentes. No puede coexistir con una media monetaria negativa sobre exactamente las mismas operaciones netas: si G y L son las sumas monetarias positivas y negativas en valor absoluto, `PF=G/L>1` implica `(G-L)/n>0`.

Ejemplo aritmético, no resultado del bot: ganar 2 USD sobre 20 USD (+10%) y perder 1 USD sobre 5 USD (−20%) produce PF 2, media monetaria +0,50 USD y media porcentual −5%. La frase «PF 1,33 y operación media negativa» necesita unidad y archivo antes de concluir que hay un error o un neto monetario negativo. El resultado Kraken a esa tarifa no fue localizado entre los resultados examinados.

### 2.2 Dos experimentos de costes, independientes y sin implementación operativa

**SUPUESTO / PROPUESTA C1: cambiar únicamente la política de entrada a maker post-only.**

- Universo: BTC, ETH, LTC, XRP, BCH y LINK; mercado USD de Kraken elegible, con el orden congelado de pares. Timeframe y señal: Donchian 55 diaria vigente.
- Después de la confirmación humana y una nueva validación de datos, señal, efectivo y riesgo: una única orden límite post-only al mejor bid vigente, redondeada al tick hacia abajo. Sin perseguir el precio ni convertirla automáticamente en taker.
- Vigencia: 10 minutos desde el envío. Rechazo post-only: no se reenvía ese día. Al vencer, cancelación del remanente y reconciliación; ante estado incierto se bloquea otro intento hasta aclararlo. Una nueva señal diaria se evalúa por las reglas originales.
- Parciales: la parte ejecutada queda protegida; el remanente se cancela al vencimiento. Si el ejecutor no puede proteger y reconciliar parciales, la variante no está habilitada para capital real.
- Stop y salida: los originales, incluida la salida de riesgo; ninguna salida de protección espera una ejecución maker. Entrada real y ATR de la vela de señal determinan el stop inicial y el tamaño máximo; el stop nunca baja.
- Tamaño: el de la implementación congelada y su límite de riesgo; el cambio de precio se refleja en cantidades, stop, comisiones y efectivo. No se aumenta riesgo para compensar entradas perdidas.

**PUBLICADO, consulta 20/10/2026:** Kraken ofrece la bandera `post` para órdenes límite [API Add Order](https://docs.kraken.com/api-reference/trading/add-order). La tabla pública consultada muestra, en el tramo inicial, maker 0,40% y taker 0,80% por lado [tarifas](https://www.kraken.com/features/fee-schedule). La tarifa efectiva depende del producto, par y tramo de la cuenta; disponer de 1.000 USD no identifica por sí solo el tramo de volumen. La tarifa de la cuenta no se verificó aquí y no se solicita ninguna credencial.

**CÁLCULO:** con esas tarifas, maker/taker suma aproximadamente 1,20% por vuelta y taker/taker 1,60%, antes de spread y deslizamiento. No son costes totales máximos. La reducción potencial es 0,40 puntos porcentuales sobre el nominal de entrada; el ahorro exacto depende de ambos nominales y de la ejecución. Maker no significa fill garantizado ni spread regalado.

**SUPUESTO / PROPUESTA C2: cambiar únicamente la admisibilidad de entrada según coste/volatilidad.**

- Es una rama separada que conserva entrada y salida taker del control; no se combina con C1.
- Regla adicional: al cierre diario, una señal Donchian 55 solo es admisible si `ATR20 / close >= 4 * c`. Se conserva la definición de ATR del código vigente. El multiplicador 4 queda fijo y no se optimiza.
- `c` es la fricción proporcional total presupuestada para una vuelta: comisiones de entrada y salida más spread y deslizamiento no incluidos ya. Una tabla de costes fechada por par y un valor conservador fijo quedan registrados antes de comparar resultados. Coste desconocido: entrada no admisible.
- Ejemplo de escenario, NO medida de ejecución: 0,80% + 0,80% de comisiones y 0,20% adicional por vuelta implican `c=1,80%` y umbral `ATR20/close >= 7,20%`.
- Salida, stop, tamaño, seis pares, orden, cuatro posiciones y controles originales se mantienen. Si no hay entradas admisibles, el resultado es ausencia de evidencia de rentabilidad, no un éxito por DD cero.

Ambas son hipótesis nuevas de ejecución o selección, no versiones aprobadas. HBAR y XLM quedan registrados como interés de Rael para otro experimento de universo; no se añaden a ninguno de estos dos ni se ocupan posiciones de alto riesgo por defecto.

### 2.3 Visión: varias IA, una decisión verificable

**SUPUESTO / PROPUESTA:** repositorio de aportes separado del operativo, como ya establece el README. Un PR por pregunta y una rama desde `main` por autor; en este PR, un único Markdown de ChatGPT.

Papeles propuestos: ChatGPT formula hipótesis y objeciones; Perplexity aporta fuentes; Meta.ai aporta contexto sin señales de ejecución; Musa mantiene referencias y estado; Claude contrasta datos, código y pruebas; Rael decide y realiza el merge. Las opiniones de varias IA que repiten la misma fuente no cuentan como evidencia independiente.

Flujo propuesto: Propuesto → Revisión → Adoptar / Adaptar / Aplazar / Rechazar. Un aporte aceptado genera una propuesta de implementación separada en el repositorio operativo, con ensayo y autorización de Rael; fusionar documentación nunca despliega ni habilita operaciones. El veredicto identifica el commit revisado. Un cambio posterior invalida la revisión de ese contenido y requiere revisión nueva.

Los aportes describen pruebas con criterios previos; los resultados posteriores son otro registro enlazado. Cada experimento referencia versión de datos, configuración, código, costes y ensayos anteriores, incluidos los negativos. Cada autor escribe solo en su carpeta. Una propuesta que requiere cambios ajenos los describe, sin realizarlos.

**COMPROBADO EN EL REPOSITORIO DE APORTES:** el guardián usa `pull_request`, permiso `contents: read` y comprueba rama, carpeta, extensiones y patrones de credenciales; las menciones a instrumentos prohibidos generan aviso. Sus comprobaciones no validan estadística, rentabilidad, autoría humana ni que solo exista un archivo. Tampoco sustituyen controles de merge. No se modificó el guardián.

**SUPUESTO / PROPUESTA:** protección de `main` con revisión y guardián obligatorios sobre el último commit, exclusión de aprobaciones obsoletas y decisión de merge reservada a Rael cuando la configuración del repositorio lo permita. No se ha comprobado que esas protecciones estén habilitadas. Las identidades de las carpetas no deben confundirse con identidades autenticadas, especialmente si varios asistentes usan la misma conexión.

## 3. Por qué debería funcionar

**SUPUESTO:** la tendencia podría explotar incorporación gradual de información y flujos persistentes; no se ha identificado una contraparte obligada a perder frente a este bot. Al cruzar spread, GOATTHEBOT compra liquidez a quien la proporciona. Post-only cambia ese intercambio: cobra menos comisión, pero se expone a cola y selección adversa. Un precio que sigue subiendo puede dejar la orden sin ejecutar precisamente en las mayores ganadoras.

**SUPUESTO:** C2 exige una escala de movimiento grande frente a la fricción. El ATR no es rentabilidad esperada ni demuestra ventaja: alta volatilidad también puede aumentar falsas rupturas y pérdidas. La regla puede fracasar dejando una muestra demasiado pequeña o peor seleccionada.

**PUBLICADO:** Bailey y colaboradores proponen evaluar el sobreajuste de backtests a partir de la selección entre candidatos, no mirando solo el ganador [The Probability of Backtest Overfitting](https://www.davidhbailey.com/dhbpapers/backtest-prob.pdf). Los protocolos de abajo son propuestas propias, todavía no ejecutadas; no se presenta un PBO calculado.

## 4. Cómo se mide

### 4.1 Evidencia reproducida y cómo repetir la comprobación

Resultados guardados examinados, con SHA-256 del ZIP completo:

| Ruta relativa a `user_data/backtest_results/exp_2026-10-14_donchian_55/` | SHA-256 |
|---|---|
| `1_d55_2018_2021_taker/backtest-result-2026-10-15_09-32-58.zip` | `8c4d31db5e2d766c118a0382ee4d8cdb37747c6d56c1f3c6c842b47689601c91` |
| `2_d55_2022_2026_taker/backtest-result-2026-10-15_09-33-18.zip` | `d55dc8b40635199bfa33c20c898ff9dfbea6484745a3006c10f7ecf21c28feb4` |

Procedimiento reproducible: lectura del JSON de resultados dentro de cada ZIP, excluyendo el JSON de configuración; tabla `strategy.EstrategiaDonchian55Diaria.trades`; `G=sum(profit_abs>0)`, `L=-sum(profit_abs<0)`, `PF=G/L`, media monetaria `sum(profit_abs)/n`. Se recalcula la concatenación, no el promedio de los PF. Todos los importes proceden de `profit_abs`, no de `profit_ratio`.

Episodio utilizado: ordenar por `open_timestamp`; unir intervalos abiertos/cerrados solapados, incluyendo contacto en el mismo instante y solapamientos transitivos; agregar `profit_abs` del componente conexo. Una posición larga que conecta otras mantiene el mismo episodio. La etiqueta precisa es «episodios no solapados», no independencia estadística demostrada. Estos conteos no prueban que el Monte Carlo previo utilizara el mismo agrupamiento.

La comprobación de canales emplea los seis archivos `user_data/data/gate/<BASE>_USDT-1d.feather`, con `high.rolling(20).max().shift(1)` y `high.rolling(55).max().shift(1)`, excluyendo filas sin ambos canales. Huellas de los datos examinados:

| Base | SHA-256 |
|---|---|
| BTC | `0a4b1ee414aac9829096ae5268f6adbe6ac34d5290d4d620db6dc27b5db31899` |
| ETH | `2f165986f8c71cb77ed38710b2c98ba3206e4d231ab12388f50926513dabf783` |
| LTC | `6c67b35058cb7ab7fb937f3b8c367965e292ea987dff5206dfb3c088357a5418` |
| XRP | `885189fd077343841910c4e81676053f53a62a5c99b52eff07cce29f3e59bf37` |
| BCH | `cb363149fab33d09af46da95fb196a660dd4eb740ad67ad41a209aebaf828f19` |
| LINK | `9c490a40d5285fa90178eeccbc8558e9a74a15cf37525ce169004c8e9d164dd1` |

**COMPROBADO LOCALMENTE:** la ventana reciente de comparación guardada contiene 33 operaciones Gate, PF 0,862275, neto −8,739827 USDT; Kraken contiene 34, PF 0,866088, neto −8,582268 USD. Los finales son 15/10 y 16/10/2026 respectivamente: una repetición de comparación entre proveedores necesita igualar también ese límite temporal. USD/USDT y distinta trayectoria de posiciones siguen siendo diferencias relevantes.

### 4.2 Prueba de selección: ¿qué significa realmente el PF 2,36?

**SUPUESTO / protocolo propuesto, antes de ejecutar:**

1. Inventario cerrado de candidatos efectivamente ensayados antes del 15/10: señales, ventanas, pares, stops y costes, con su cronología. No crear una cuadrícula nueva para fingir que representa la búsqueda original. Duplicados semánticos como 55 y 20 Y 55 cuentan una vez; variantes conocidas y abandonadas se conservan.
2. Reproducir cada candidato comparable sobre el mismo periodo, capital y contabilidad de costes, sin alterar sus reglas. No rellenar historial inexistente con precios sintéticos. Registrar elegibilidad histórica; elegir hoy seis supervivientes limita la generalización aunque no haya sesgo de código.
3. Una matriz diaria conjunta por candidato: cambio neto de equity marcado a mercado dividido por su capital inicial. Días sin posiciones aportan cero y se informa tiempo activo. El criterio de selección original se reproduce si quedó registrado; si no, se declara desconocido y no se calcula un PBO pretendidamente exacto.
4. Diagnóstico de multiplicidad mediante contraste bootstrap del máximo de medias: centrar cada serie diaria restando su media, remuestrear bloques circulares conjuntos de 90 días para todos los candidatos, 10.000 réplicas y semilla 20261020. Comparar el máximo observado de medias con el máximo de cada réplica bajo el nulo. Sensibilidad fijada en bloques de 30 y 180 días, sin escoger después el resultado favorable. Es un contraste aproximado de una familia reconstruida; no una prueba de causalidad ni una nueva simulación del motor de riesgo.
5. Evaluación separada de 2018–2021 con la versión que existía antes de abrir esa reserva y evidencia de fecha. El tramo de selección 2022–2026 no se vuelve a llamar fuera de muestra. Una simulación continua se informa aparte; las posiciones que crucen una frontera no se cortan arbitrariamente sin declarar esa decisión.

**Éxito diagnóstico propuesto:** familia reconstruida de manera suficiente, p ajustado <=0,05 con bloques 90 y sensibilidad consistente en 30 y 180; reserva no contaminada con PF neto >=1,3 y neto monetario positivo. Esto reduce explicaciones por selección bajo los supuestos del contraste, pero no certifica ventaja futura.

**Fracaso de la afirmación de robustez:** reserva válida con neto <=0 o PF <1,3. **Evidencia insuficiente:** búsqueda no reconstruible, reserva reutilizada, p >0,05 o conclusión dependiente del bloque. No rechazar el nulo no demuestra ausencia de ventaja; tampoco autoriza afirmar que existe. No hay prueba que recupere un conjunto verdaderamente virgen una vez consultado.

### 4.3 ¿Deterioro o ruido? Método inmediato con resultado de tres estados

**SUPUESTO / protocolo propuesto:** congelar el corte 01/01/2022 ya señalado, sin buscar una fecha de ruptura óptima. Reconstruir P&L diario neto y capital comparable, incluidos no realizados y días inactivos. Definir `Delta = media_diaria_2022_en_adelante - media_diaria_2018_2021`.

Bootstrap por bloques circulares dentro de cada tramo, con los mismos bloques 90/30/180, 10.000 réplicas y semilla 20261020; conservar todos los activos conjuntamente. Intervalo percentil bilateral del 95% para Delta y límite inferior unilateral del 95% de la media reciente. Las tres sensibilidades forman un diagnóstico, no tres oportunidades de elegir significación. No se infieren independencia ni normalidad de 161 trades. El tamaño informativo se reporta como 23/31 episodios y duración de los episodios, además de operaciones.

- **Deterioro estadísticamente apoyado:** límite superior del intervalo de Delta <0 en las tres sensibilidades.
- **Ventaja reciente apoyada bajo el modelo:** límite inferior reciente >0, PF reciente >=1,3 y ausencia de contradicción entre sensibilidades. Puede coexistir con deterioro: ganar menos y seguir ganando son preguntas distintas.
- **Inconcluso:** intervalos que atraviesan cero, pocos bloques efectivos o resultados sensibles al bloque. No equivale a «régimen estable».

La misma matriz se calcula antes y después de costes como descomposición contable, manteniendo las operaciones, sin presentar la versión bruta como estrategia operable. Si el bruto se mantiene y cae el neto, los costes son una explicación contable; si caen ambos, no bastan para explicar el deterioro. El corte reciente dic 2024–oct 2026 ya fue elegido mirando resultados: es advertencia exploratoria, no una segunda prueba confirmatoria independiente.

Como diagnóstico descriptivo de régimen, se añaden volatilidad y eficiencia de tendencia de BTC calculadas exclusivamente con los 90 días anteriores a cada entrada. No se convierten en filtros ni se buscan umbrales. Una asociación con ellas no establece causalidad. La hipótesis de cambio estructural puede seguir sin distinguirse del ruido; el método aprovecha datos existentes, no promete crear información adicional. El seguimiento prospectivo mensual informa exposición, discrepancias, costes y episodios, sin repetir contrastes al 5% cada mes para declarar victoria.

### 4.4 Criterios previos de C1 y C2

**SUPUESTO / protocolo común:** experimentos separados contra el control vigente; capital 1.000, seis pares, orden y límites congelados, costes de Kraken por lado claramente diferenciados. Reejecución completa de la cartera cuando cambien fills o entradas: restar comisiones de operaciones ya seleccionadas solo es diagnóstico, porque efectivo, tamaño y bloqueos podrían cambiar.

Desarrollo: 2022–24/09/2026, declarado consultado. Comprobación histórica de sensibilidad: 2018–2021 y datos Kraken disponibles, también declarados consultados; ninguna se etiqueta como una reserva nueva. La evidencia posterior empieza tras registrar este protocolo y disponer del registro necesario. Sin libro de órdenes histórico suficiente, C1 no recibe un backtest de fills inventados. Los ensayos se mantienen fuera de los procesos, datos operativos y archivos congelados de Fase 1.

**Éxito histórico provisional por variante:** neto monetario positivo, PF >=1,3, neto mayor que el control y DD <10%, tanto en todo el desarrollo como en su subtramo reciente común disponible. A igualdad de capital; sin aumentar asignación para aparentar mejora. Menos de 20 episodios completados en una muestra implica evidencia insuficiente para aceptarla económicamente aunque las cifras pasen. Ese mínimo es un suelo propuesto, no una garantía de potencia. El tramo corto puede impedir aprobar: esa posibilidad es deliberada.

**Incertidumbre y selección entre dos variantes:** comparación pareada del cambio neto diario contra control, bootstrap de bloques como arriba; p de mejora ajustados con Holm para los dos experimentos. Aceptación económica requiere mejora positiva apoyada al nivel conjunto 5%; si no, resultado inconcluso. Los umbrales de este aporte no sustituyen la aprobación de Rael ni el expediente de riesgo original.

**C1, evidencia específica:** al menos 60 días de captura pública continua de cotizaciones y trades, con fecha, y simulación de órdenes que incluya tiempo de confirmación humana. Fill conservador solo con trades posteriores al envío estrictamente por debajo del límite de compra y volumen suficiente después de una reserva de cola basada en profundidad observada; no basta que una vela toque el precio. Sin profundidad válida no se acredita un fill. Se conservan señales no ejecutadas, capital ocioso y ganadoras perdidas. No hay mínimo artificial de fills para demostrar ventaja; pocos fills llevan a «insuficiente». Esta simulación no certifica posición real en cola. Los parciales requieren ensayos específicos del ejecutor antes de cualquier habilitación real.

**C1, fracaso:** PF <1,3, neto <=0, pérdida de las mayores tendencias que haga el neto inferior al control, o mejora que desaparece al excluir fills meramente tocados o al modelar demora humana. No se aprueba una tarifa maker asignada a todos los fills sin evidencia.

**C2, evidencia específica:** misma entrada taker del control; se aplica solo el filtro fijo. La tabla `c` incluye el tramo base sin descuentos por generar actividad y se fija antes del cálculo; se declara un escenario de estrés con 0,10 puntos porcentuales adicionales por lado, aplicado a control y variante. Éxito requiere mantener neto >0 y PF >=1,3 también en ese estrés. No se cambian 4, ATR20 o el universo tras ver resultados.

**C2, fracaso:** neto <=0, PF <1,3, neto inferior al control o fallo del estrés. Menos de 20 episodios o mejora estadística no apoyada: insuficiente, no éxito. Si ninguna variante cumple, la conclusión propuesta es aplazar capital real; subir tamaño, aflojar límites o generar volumen para conseguir descuentos no arregla una expectativa negativa.

### 4.5 Pruebas del flujo de aportes

**SUPUESTO / aceptación propuesta:** un PR válido de documentación pasa; rama/carpeta indebida, archivo no permitido o cambio del workflow fallan; un push posterior invalida el veredicto anterior; la integración de documentación no inicia despliegues ni habilita trading. El guardián actual ya cubre parte de esto, no todo. La prueba de detección de secretos puede usar patrones sintéticos desechables fuera del historial compartido, nunca credenciales reales.

**PUBLICADO:** GitHub documenta riesgos de ejecutar contenido no confiable con privilegios en `pull_request_target` [guía de seguridad](https://docs.github.com/en/actions/reference/security/securely-using-pull_request_target). La propuesta conserva validación de documentación sin ejecutar código adjunto ni aceptar instrucciones contenidas en aportes como autorizaciones. El resultado verde significa «cumple esas comprobaciones», no «estrategia aprobada».

## 5. Supuestos y lo que no sabes

- SUPUESTO: importes `profit_abs`, timestamps y pares de los ZIP representan fielmente las simulaciones originales. Se recalcularon estadísticas, no se reconstruyó aquí todo el backtest desde precios.
- SUPUESTO: el historial completo de candidatos y de cuándo se consultó cada periodo está recuperable; no está demostrado. Sin él no se publica una probabilidad exacta de sobreajuste.
- MEDIDO APORTADO: controles, 5 ensayos sin bróker, paquete Kraken y 86/89 coincidencias de señal. No se volvieron a ejecutar ni se certificó una conexión real con Kraken.
- DESCONOCIDO: artefacto web de Claude, no accesible en esta sesión; no se atribuye contenido no leído. Fuentes utilizadas: memorándum, convocatoria y archivos locales identificados.
- DESCONOCIDO: tarifa específica de la cuenta, libro histórico, demora humana y cola real de C1. La documentación de post-only no demuestra que el adaptador instalado lo configure correctamente.
- SUPUESTO: el bootstrap por bloques aproxima dependencia y estabilidad dentro de cada tramo; las colas y episodios muy largos pueden invalidar esa aproximación. Pocos datos pueden dejar todos los contrastes inconclusos.
- La equivalencia 20 Y 55 requiere mismos precios, ventanas anidadas y calentamiento completo; no se generaliza a otra implementación.

## 6. Riesgos

Selección entre variantes, activos supervivientes, cambio de proveedor, USD frente a USDT, stops intravela optimistas, demoras de confirmación, selección adversa maker y concentración en pocas tendencias. Reducir costes no crea ventaja bruta. Aumentar volatilidad no garantiza movimientos capturables.

El reparto por operación puede acumular exposición consolidada muy superior al 30%; no se presenta como diversificación agregada ni se cambia en estos experimentos. El máximo drawdown histórico de una simulación concatenada no es el de una cartera continua. Un P95 no es un límite garantizado y un kill switch puede ejecutarse después del umbral.

En colaboración: carpetas que aparentan autoría sin autenticarla, revisión de un commit distinto del fusionado, conflictos concurrentes, fuentes inventadas repetidas por varias IA, resultados de pruebas declarados sin artefactos y datos privados en texto o imágenes. El guardián no detecta todos esos casos. Los cambios de permisos o protecciones requerirían una decisión separada; este aporte no los aplica.

## 7. Encaje con las reglas

Este aporte propone revisión y experimentos: solo spot y solo largos, sin apalancamiento, margen, futuros ni perpetuos. La señal, los archivos congelados, la configuración y el reloj de Fase 1 quedan intactos. No se cambia el universo operativo; HBAR y XLM son una propuesta pendiente de validación separada.

No se envían órdenes, no se habilita dinero real, no se solicitan ni incluyen credenciales y no se modifican permisos. C1 y C2 cambian una variable cada uno y no se combinan. Claude conserva el papel de verificación y Rael la decisión; este documento no contiene órdenes dirigidas a otra IA.

Entrega: un archivo en `aportes/chatgpt/`, rama desde `main`, PR para revisión, sin merge. Los protocolos aún no ejecutados están marcados como SUPUESTO y ningún resultado propuesto se presenta como medido.

