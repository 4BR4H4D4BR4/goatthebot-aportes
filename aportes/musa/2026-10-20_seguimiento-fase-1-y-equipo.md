TÍTULO: Seguimiento de la Fase 1, costumbres del equipo en GitHub y visión de la colaboración
AUTOR: Musa
FECHA: 2026-10-20
TIPO: visión / revisión
RESPONDE A: Convocatoria 2026-10-19, sección 10 (encargo a Musa: seguimiento, coordinación y visión)

## 1. Resumen

Propongo un seguimiento semanal de solo lectura de la Fase 1 hasta el 29 de noviembre: una lista de verificación fija de integridad, concordancia y riesgo, con escalación inmediata a Rael ante cualquier discrepancia, y un informe de cierre contra los cinco criterios de paso a la Fase 2. Propongo además las costumbres de trabajo del equipo en este repositorio (ramas, archivos, veredictos, calendario de convocatorias) y tres proyectos de visión que solo arrancarían tras cerrar la Fase 1. Nada de esto toca la ficha congelada ni propone operaciones.

## 2. Propuesta

### A. Seguimiento de la Fase 1 (hasta el 29 de noviembre, día 42)

**Informe semanal** (uno por semana, máximo una página, solo semáforos y cambios). Lo compila Musa a partir del registro de decisiones por par y día y del informe con cálculo de referencia que ya genera el sistema. Contenido fijo:

1. **Integridad:** el MD5 de la ficha sigue siendo el registrado; sin reinicios del bot sin explicación; datos diarios de Gate.io completos en los 6 pares (sin velas que falten).
2. **Concordancia:** decisiones del bot frente al cálculo de referencia. Objetivo: cero discrepancias sin explicar.
3. **Riesgo observado:** riesgo abierto total frente al tope del 2%; drawdown desde el pico frente al kill switch del 10% y frente a la banda de Monte Carlo (P95 de 6,7%, medido en la compuerta 0→1).
4. **Exposición por sub-cartera:** porcentaje comprometido de cada bloque (55/30/15), como métrica observada. Responde al problema abierto (d) del memorándum: un ensayo llegó al 122,9% de un bloque. Se observa y se reporta; no se propone ningún cambio, porque la ficha está congelada.
5. **Actividad:** operaciones abiertas y cerradas en la semana y acumulado, comparado con lo esperado (unas 18 al año según el memorándum). SUPUESTO: ese ritmo no es uniforme en el tiempo; la comparación es orientativa, no un criterio.
6. **Incidentes:** contador de días seguidos sin incidentes críticos, mirando a los 14 días finales que exige el paso de fase.
7. **Estado de los aportes:** tabla de aportes del equipo con su veredicto y siguiente paso (ver parte B).

**Quién revisa qué:** Musa compila, ordena y publica el informe en este repositorio, en su carpeta, y mantiene el contador de criterios. Claude verifica cualquier cifra que no cuadre (es su papel de CTO y dueño del cálculo de referencia). Rael lee el informe y decide.

**Escalación inmediata a Rael** (el mismo día, sin esperar al informe semanal):

- Cualquier discrepancia entre el bot y el cálculo de referencia que no tenga explicación en 24 horas.
- Un MD5 distinto del registrado, o un reinicio del bot sin causa clara.
- Un hueco de datos de más de una vela diaria en cualquier par.
- El drawdown entra en la cola de Monte Carlo (supera el P95 de 6,7%). SUPUESTO: uso ese P95, medido en backtest, como umbral de aviso, no de acción.
- Cualquier incidente crítico, porque rompe la racha de 14 días.

**Informe de cierre (29 de noviembre):** los cinco criterios de la sección 2 del memorándum, uno por uno, con veredicto "cumple / no cumple / sin evidencia": 6 semanas completas; 14 días seguidos sin incidentes críticos al final; ninguna discrepancia sin explicar; drawdown dentro del rango de Monte Carlo; y el sí de Rael, que es suyo y no se sustituye. El informe separa dos frases que no deben mezclarse: "el bot funcionó sin fallos" y "el edge no está probado" (con 2 o 3 operaciones, la Fase 1 valida el bot, no el edge, como dice la sección 6b del memorándum).

### B. Costumbres del equipo en GitHub

Sobre las reglas que ya fija el README, propongo estas costumbres concretas:

- **Ramas:** una rama por aporte, con el nombre ya normado `aporte/<carpeta>/<tema>` en minúsculas y guiones. La rama se borra al cerrarse su Pull Request, haya merge o rechazo. Nunca se reutiliza una rama para otro tema.
- **Archivos:** un solo archivo por aporte, `aportes/<carpeta>/AAAA-MM-DD_<tema>.md`, con el mismo tema de la rama. Los informes semanales de seguimiento son la excepción práctica: uno por semana, `AAAA-MM-DD_informe-semanal-NN.md`, para que el historial de la Fase 1 quede fechado y ordenado.
- **Plantilla:** se usa la vigente sin cambios. Como costumbre adicional, cada aporte abre con su campo RESPONDE A (convocatoria o aporte anterior) para que la cadena de decisiones se pueda seguir sin buscar.
- **Calendario de convocatorias:** una convocatoria vigente a la vez, ligada a un hito (cierre de fase o un problema abierto de la sección 6), no a una fecha fija del mes. Ventana de aportes: 7 días desde su publicación. Ventanas siguientes sugeridas: cierre de la Fase 1 (29 de noviembre) y, si Rael lo decide, apertura de la Fase 2.
- **Veredictos:** Claude comenta cada Pull Request empezando por una sola palabra: Adoptar, Adaptar, Aplazar o Rechazar, seguida de un motivo de cinco líneas como máximo que incluya la cifra o el hecho que decide. Plazo: 7 días desde el aporte.
  - *Adaptar* se resuelve con una versión corregida en la misma rama, no con un archivo nuevo.
  - *Aplazar* lleva escrita en el comentario su fecha de revisión; sin fecha, cuenta como rechazo amable y Musa lo marca así en su tabla.
  - *Rechazar* cierra el Pull Request sin merge, con el motivo guardado: el historial de rechazos es parte de la memoria del equipo.
  - Solo Rael hace merge, como ya dice el README.
- **Tabla viva de estado:** Musa mantiene en su informe semanal la lista de aportes abiertos con autor, fecha, veredicto, motivo corto, siguiente paso y dueño de ese paso. Si un aporte cumple 14 días sin veredicto, Musa lo escala a Rael en el informe.
- **Meta.ai:** cuando Meta.ai entregue un aporte a Musa, Musa lo sube tal cual, sin editarlo, desde la rama `aporte/meta/<tema>` al archivo `aportes/meta/AAAA-MM-DD_<tema>.md` con AUTOR: Meta.ai. Cualquier comentario de Musa sobre ese aporte va en un aporte propio y separado, nunca dentro del archivo de Meta.ai.

### C. Visión: qué más podría salir de esta colaboración

Tres proyectos, en este orden, y ninguno arranca antes del cierre de la Fase 1:

1. **Bitácora abierta de experimentos.** Publicar, solo de histórico cerrado, las fichas de lo probado con su criterio fijado antes y su resultado, incluidos los fracasos (Raschke: −70,94%; la confluencia anti-predictiva; Donchian con 9 pares). Hace falta: la decisión de Rael sobre qué se publica y cuándo (nunca nada de una fase en curso), la revisión de Claude de cada cifra, y un repositorio público separado de este.
2. **El método KabbaL como plantilla reutilizable.** Documentar el ciclo que este repositorio ya practica (convocatoria, aportes con plantilla, guardián automático, veredicto con motivo, merge humano) para aplicarlo a otros proyectos del dueño con el mismo equipo de IAs. Hace falta: dos o tres ciclos completos de convocatoria aquí, como evidencia de que el método aguanta, y una guía escrita por Musa con revisión de Claude.
3. **Tablero de solo lectura de los proyectos del equipo.** Extender la idea del centro de operaciones local: un panel que lea archivos de estado simples de cada proyecto (como este repositorio) y muestre estado, hitos y veredictos pendientes. Hace falta: que cada proyecto mantenga un archivo de estado con formato común, y la decisión de Rael sobre el alcance. Sin claves y sin funciones de ejecución, igual que el panel actual.

Lo que la visión no incluye: otro bot, otra estrategia, ni ningún ingreso todavía. SUPUESTO: monetizar algo antes de cerrar la Fase 2 sería prematuro.

## 3. Por qué debería funcionar

El riesgo práctico de la Fase 1 no es la estrategia, que está congelada, sino el silencio: seis semanas en las que un fallo barato de detectar (una discrepancia, un hueco de datos, un reinicio) puede descubrirse al final, cuando ya invalidó la fase. Una revisión semanal fija convierte ese riesgo en seis puntos de control que cuestan una página cada uno. En el equipo pasa lo mismo a otra escala: cinco IAs que no comparten memoria necesitan que el repositorio sea la memoria, y un repositorio solo es memoria si cada pieza tiene dueño, formato, veredicto y fecha. Eso es lo que estas costumbres garantizan. La visión, por último, parte de un activo que ya existe y casi nadie construye: un registro fechado y verificado de decisiones, con sus fracasos incluidos.

## 4. Cómo se mide

- **Seguimiento semanal.** Éxito: los 6 informes entregados en su semana, y toda discrepancia escalada a Rael en un máximo de 24 horas desde que aparece en los datos que Musa recibe. Fracaso: dos informes seguidos sin entregar, o una discrepancia que llegue al 29 de noviembre sin haberse escalado.
- **Informe de cierre.** Éxito: entregado el 29 de noviembre con los cinco criterios evaluados uno a uno y con la separación explícita entre funcionamiento del bot y prueba del edge. Fracaso: un cierre que declare la fase "buena" en general sin pasar por cada criterio.
- **Costumbres de GitHub.** Éxito, medido en la próxima convocatoria: el 100% de los aportes en formato y el 100% con veredicto comentado en 7 días o menos. Fracaso: cualquier aporte que llegue a 14 días sin veredicto.
- **Visión.** No se mide ahora. Criterio fijado de antemano: si la Fase 1 cierra con su informe completo, en diciembre se redacta la guía del proyecto 2 de la visión; si no, la visión se archiva sin ruido.

## 5. Supuestos y lo que no sabes

- SUPUESTO: Musa recibirá con regularidad el registro de decisiones y el informe de referencia del paper. Si esos datos llegan solo al final, la escalación en 24 horas corre desde la recepción, no desde el hecho, y el seguimiento pierde gran parte de su valor. Es la primera cosa a verificar en el informe de la semana 1.
- SUPUESTO: el P95 de drawdown de Monte Carlo (6,7%) medido en la compuerta sirve como banda de aviso también para el paper. Es una referencia de backtest trasplantada, no una medición del paper.
- SUPUESTO: el equipo prefiere convocatorias por hito a convocatorias mensuales fijas. Nadie lo ha votado; lo propongo por el ritmo de fases del proyecto.
- Musa no ha medido ninguna cifra de trading en este aporte. Todas las cifras citadas (profit factor 2,36; P95 de 6,7%; −70,94%; 122,9% de bloque; unas 18 operaciones al año) vienen del memorándum de Rael y Claude del 19 de octubre de 2026 y no son mediciones propias.
- No sé si Claude ya emite el informe de referencia en un formato que Musa pueda leer directamente, ni si Rael prefiere recibir el informe semanal primero en el chat y luego en el repositorio. Lo dejo preguntado aquí, no resuelto.

## 6. Riesgos

- **Fatiga de informes.** Seis Pull Requests de informe en seis semanas pueden volverse ruido que nadie lee. Mitigación: una página como máximo, solo semáforos y cambios; si una semana no cambia nada, el informe lo dice en tres líneas.
- **Lectura falsa del cierre.** Una Fase 1 limpia puede leerse como "la estrategia funciona", cuando con 2 o 3 operaciones solo prueba que el bot funciona. Mitigación: la separación obligatoria de las dos frases en el informe de cierre.
- **Seguimiento sin datos.** Si el registro del paper no llega a Musa, el seguimiento sería ficticio y peor que no tenerlo, porque daría una falsa sensación de control. Mitigación: el informe de la semana 1 verifica primero el acceso a los datos, y si no existe, este aporte se retira y se dice por qué.
- **Distracción por la visión.** Los tres proyectos de visión pueden competir por atención con el bot. Mitigación: ninguno arranca antes del 29 de noviembre y cada uno necesita su propio sí de Rael.

## 7. Encaje con las reglas

Este aporte es coordinación y seguimiento, desde el papel que el memorándum asigna a Musa: no propone ejecutar operaciones ni cambiar la estrategia. Respeta las reglas del README: solo spot y solo largos en todo lo propuesto, sin apalancamiento; no toca nada de la ficha de la Fase 1, porque el seguimiento es de solo lectura; no propone ningún paso hacia dinero real, solo medir los criterios de paso que el memorándum ya fijó, y cualquier decisión sobre la Fase 2 sigue siendo de Rael; no contiene ninguna clave, contraseña ni token; todo dato no medido por Musa va marcado como SUPUESTO y las cifras ajenas se atribuyen al memorándum; no cambia ninguna variable del bot, así que no rompe la regla de una variable por experimento. Es una propuesta: Claude la verifica y Rael decide.
