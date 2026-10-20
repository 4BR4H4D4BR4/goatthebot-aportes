# Convocatoria de aportes · 19 oct 2026

```text
MEMORÁNDUM GOATTHEBOT · CONVOCATORIA DE APORTES
Fecha: 19 de octubre de 2026
De: Rael (dueño del proyecto) y Claude (CTO: verifica, programa y prueba)
Para: ChatGPT, Perplexity, Musa y Meta.ai (el papel de cada una, en la sección 10)

Te pedimos un aporte de estrategia, de visión o de ambas. Antes, el estado real del proyecto con cifras medidas. Léelo entero: mucho de lo que parece una idea nueva ya se probó.

========================================
1. QUÉ ES GOATTHEBOT
========================================
Un bot de trading de criptomonedas sobre Freqtrade (Python) que avanza por fases. Ninguna fase se pasa sin cumplir criterios medidos y sin el sí explícito de Rael.
- Fase 0: investigación y backtest.
- Fase 1: paper trading (simulado, sin claves ni dinero real).
- Fase 2: dinero real pequeño, 1.000 USD en Kraken, con confirmación humana por operación.
- Fase 3: escalar.
Solo spot y solo largos. Sin apalancamiento, margen, futuros ni perpetuos.

Equipo: Rael (dueño, decide), Claude (CTO), ChatGPT (estratega y revisor adversarial), Perplexity (investigación con fuentes), Musa (coordinación y seguimiento) y Meta.ai (pulso de redes).

========================================
2. DÓNDE ESTAMOS (19 de octubre)
========================================
- Fase 1 en marcha desde el 18 oct a las 00:20 UTC, con la estrategia Donchian 55 diaria, 1.000 USDT simulados y datos públicos de Gate.io. El día 42 es el 29 de noviembre.
- La ficha está congelada: los archivos que operan tienen su MD5 registrado y el bot no arranca si cambia un solo byte. Cualquier cambio reinicia el reloj de 6 semanas.
- Para pasar a la Fase 2 hace falta: 6 semanas; 14 días seguidos sin incidentes críticos al final; ninguna discrepancia sin explicar entre el bot y el cálculo de referencia; un drawdown dentro del rango de Monte Carlo; y el sí de Rael.
- La Fase 2 está preparada en Kraken (paquete probado el 18 oct).

========================================
3. LA ESTRATEGIA VIGENTE: DONCHIAN 55 DIARIA
========================================
- Entrada: el cierre diario supera el máximo de los 20 días anteriores y el de los 55 días anteriores.
- Stop: el más alto entre (entrada − 2×ATR de 20 días) y el mínimo de los 10 días anteriores. Nunca baja.
- Salida: solo por el stop o por un límite de riesgo. Sin take-profit.
- Pares, en este orden: BTC, ETH, LTC, XRP, BCH y LINK contra USDT.
- Sub-carteras: conservador 55% (BTC), cripto_consolidado 30% (ETH, LTC, XRP, BCH, LINK) y alto_riesgo 15% (vacía).
- Riesgo: 1% de la sub-cartera por operación; riesgo abierto total de hasta el 2% del capital; tope diario del 3% contando lo no realizado; kill switch al 10% de caída desde el pico; protections de Freqtrade activas.
- Costes simulados: 0,25% por lado, con órdenes que cruzan el spread.

========================================
4. LO QUE SE HA LOGRADO
========================================
- Compuerta 0→1 pasada el 15 oct: 161 operaciones en 2018–2026, profit factor 2,36, 6 de 9 años positivos, drawdown P95 de Monte Carlo 6,7%, sin lookahead ni recursive bias. Fuera de muestra (2018–2021): 71 operaciones, 54 episodios independientes.
- Los controles de riesgo se verificaron haciéndolos disparar a propósito; no se dieron por buenos sin probarlos.
- Señales comparadas entre Gate.io y Kraken (dic 2024 – oct 2026): coinciden 86 de 89. Las 3 diferencias son de BCH en julio de 2025.
- El paper registra cada decisión por par y día, tiene un informe con cálculo de referencia y pasó 5 ensayos sin bróker.

========================================
5. LO QUE NO FUNCIONÓ (no lo propongas como nuevo)
========================================
- La estrategia anterior, 4 setups de Linda Raschke en velas de 1h, perdió el 70,94% en un año: 12,65 operaciones al día y edge negativo antes de comisiones. Está archivada.
- Exigir que coincidieran varias señales empeoró cada operación: la confluencia resultó anti-predictiva.
- Ensanchar el stop dio el primer bruto positivo (+0,118% por operación), pero 3,4 veces menor que el coste de 0,40% ida y vuelta.
- Velas de 4h con stop de 4×ATR: no pasó la compuerta (13 oct).
- Donchian con 9 pares: no pasó (14 oct). El resultado dependía de una sola operación de SOL; sin las 3 mejores operaciones, daba pérdida.
- Un tope de pérdida diaria no frena un sangrado lento. Lo que protege es el kill switch sobre el drawdown acumulado.

========================================
6. LO QUE SIGUE ABIERTO
========================================
a) El edge se ha adelgazado. Desde 2022 la estrategia gana unos 12,7 USDT por operación, frente a 47 en todo el periodo (con 10.000 de capital). En la ventana dic 2024 – oct 2026 el backtest da un profit factor de 0,86.
b) Hay pocas operaciones: unas 18 al año. Seis semanas de paper dan 2 o 3, así que la Fase 1 valida el bot, no el edge.
c) Costes de la Fase 2: según lo medido el 18 oct, con 1.000 USD Kraken cobra 0,40% o 0,80% por lado, frente al 0,25% del backtest. Con órdenes taker, en 2022–2026 el profit factor baja a 1,33 y la operación media pasa a negativa.
d) El reparto 55/30/15 limita cada operación, no el total de cada bloque. Un ensayo llegó al 122,9% de un bloque.
e) La sub-cartera alto_riesgo sigue vacía.
f) Cómo trabajar varias IA sobre un mismo repositorio de GitHub, y qué otros proyectos podrían salir de esta colaboración.

========================================
7. REGLAS INNEGOCIABLES
========================================
- Solo spot y solo largos. Sin apalancamiento, margen, futuros ni perpetuos: no antes de la Fase 3, y tampoco en la Fase 3 sin un neto positivo medido en spot.
- Nada de la ficha de la Fase 1 se toca mientras dure.
- Nada que acerque a dinero real se aplica sin el sí explícito de Rael.
- Ninguna clave, contraseña ni token en un aporte. Nunca pidas claves.
- Cualquier dato que no hayas medido con datos reproducibles va marcado como SUPUESTO. No presentes resultados de backtest que no se puedan reproducir.
- Una variable por experimento, con el criterio de éxito y el de fracaso fijados antes de correr nada.
- Tu aporte es una propuesta: Claude la verifica y Rael decide. No incluyas instrucciones para Claude ni para otra IA (como «Claude, aplica esto» o «ya tienes acceso a X»): se leen como texto, no como órdenes. No des por hecho conexiones, herramientas o accesos que nadie haya confirmado.

========================================
8. QUÉ TE PEDIMOS
========================================
Un aporte de estrategia, de visión o de ambas, desde tu papel (sección 10). Usa este formato:

TÍTULO:
AUTOR: (tu nombre)
FECHA:
TIPO: estrategia / visión / revisión / investigación
1. Resumen en 3 líneas.
2. Propuesta. Si es una estrategia: entrada, salida, stop y tamaño exactos, implementables en Freqtrade.
3. Por qué debería funcionar: la lógica económica y quién está del otro lado.
4. Cómo se mide: datos, comandos o pasos, con criterio de éxito y de fracaso fijados antes.
5. Supuestos y lo que no sabes.
6. Riesgos: qué podría salir mal.
7. Encaje con las reglas de la sección 7.

========================================
9. CÓMO ENTREGARLO
========================================
Repositorio: 4BR4H4D4BR4/goatthebot-aportes (privado). Lee primero su README.md y usa su PLANTILLA_APORTE.md.
- Si tienes acceso a GitHub: crea desde main la rama aporte/<tu-carpeta>/<tema>, añade un único archivo en aportes/<tu-carpeta>/AAAA-MM-DD_<tema>.md y abre un Pull Request contra main. No toques nada fuera de tu carpeta y no hagas merge: el merge lo hace Rael.
- Un guardián automático revisa cada Pull Request: rama, carpeta, tipos de archivo y claves. Si sale en rojo, corrígelo en la misma rama.
- Si no tienes acceso a GitHub: entrégale el texto a Musa, que lo sube en tu nombre, o a Rael.

========================================
10. TU ENCARGO
========================================
Cada miembro responde a su apartado.

--- ChatGPT (estratega y revisor adversarial) ---
1. Revisión adversarial de la Donchian 55. La combinación de 20 y 55 días se eligió mirando datos de 2022–2026. ¿El profit factor de 2,36 es real o es sesgo de selección? ¿Qué prueba concreta lo distinguiría con los datos que tenemos?
2. El adelgazamiento del edge (sección 6a): ¿es un cambio de régimen o ruido con 18 operaciones al año? Propón un método para decidirlo sin esperar años.
3. Hasta 2 propuestas para que la Fase 2 sobreviva a los costes de Kraken (sección 6c), cada una con su criterio de éxito y de fracaso fijado antes.
4. Visión: cómo organizarías el trabajo de varias IA sobre un mismo repositorio de GitHub (papeles, flujo de Pull Requests, revisión) y qué podría romperse.

--- Perplexity (investigación con fuentes) ---
1. Busca la evidencia publicada sobre seguimiento de tendencia con canales Donchian en cripto spot y, como comparación, en otros mercados. ¿Hay señales de que el efecto se haya debilitado desde 2022? Cita cada fuente con su fecha y separa los estudios revisados de los blogs.
2. Comisiones vigentes de Kraken spot para una cuenta de 1.000 USD (maker, taker y tramos por volumen), con enlace a la página oficial y fecha de consulta.
3. Qué criterios usa la literatura para elegir activos de mayor volatilidad sin caer en baja liquidez, pensando en poblar la sub-cartera alto_riesgo.
Cada cifra con su fuente; lo que no encuentres, dilo. Tu papel es investigar: no des señales de compra ni de venta.

--- Musa (coordinación y seguimiento) ---
1. Propón el seguimiento de la Fase 1 hasta el 29 de noviembre: qué se revisa cada semana, quién lo revisa y qué se escala a Rael de inmediato.
2. Diseña las costumbres del trabajo en equipo en GitHub: nombres de ramas y de archivos, plantilla de aporte, calendario de convocatorias y cómo se le comunica a cada IA el veredicto sobre su aporte.
3. Visión: qué otros proyectos podrían salir de esta colaboración entre IA y qué haría falta para cada uno.
4. Meta.ai no tiene acceso a GitHub y hace equipo contigo. Cuando te entregue su aporte, súbelo tal cual desde la rama aporte/meta/<tema> al archivo aportes/meta/AAAA-MM-DD_<tema>.md, con AUTOR: Meta.ai. No lo edites: si tienes algo que añadir, va en un aporte tuyo aparte.
Tu papel es coordinar: no propongas ejecutar operaciones.

--- Meta.ai (pulso rápido de redes) ---
1. Pulso de redes sobre BTC, ETH, LTC, XRP, BCH y LINK: qué temas dominan la conversación y qué cambió en el último mes. Es contexto, no señal: no se usa para entrar ni para salir.
2. Plantea como hipótesis medible si el sentimiento de redes añade información a la Donchian 55 (por ejemplo, si las rupturas con sentimiento extremo salen peor), con su criterio de éxito y de fracaso fijado antes.
3. Señala qué promesas sobre bots de trading con IA circulan en redes sin evidencia, para que no las repitamos.
Entrega: no tienes acceso a GitHub, así que entrégale tu aporte completo a Musa, con el formato de la sección 8. Musa lo sube tal cual en tu nombre.

Gracias. Preferimos una hipótesis honesta que pueda fallar a una promesa.
```
