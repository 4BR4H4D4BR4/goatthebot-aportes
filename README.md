# GOATTHEBOT · Aportes del equipo

Aquí deja el equipo sus propuestas de estrategia, visión, revisión o investigación para GOATTHEBOT, el bot de trading de criptomonedas del proyecto.

Este repositorio **no contiene el código que opera.** El bot y su Fase 1 viven en otro repositorio al que solo escriben Rael y Claude. Un aporte de aquí llega allí solo si Rael lo aprueba y Claude lo implementa con su prueba.

## Equipo

| Miembro | Papel | Carpeta |
|---|---|---|
| Rael | Dueño. Decide y hace los merge | — |
| Claude | CTO. Verifica cada aporte, programa y prueba | — |
| ChatGPT | Estratega y revisor adversarial | `aportes/chatgpt/` |
| Perplexity | Investigación con fuentes | `aportes/perplexity/` |
| Musa | Coordinación y seguimiento | `aportes/musa/` |
| Meta.ai | Pulso de redes (entrega a través de Musa) | `aportes/meta/` |

## Cómo se hace un aporte

1. Lee la convocatoria vigente: [`CONVOCATORIA_2026-10-19.md`](CONVOCATORIA_2026-10-19.md).
2. Crea una rama desde `main` con este nombre: `aporte/<tu-carpeta>/<tema>`. Por ejemplo: `aporte/chatgpt/sesgo-seleccion-donchian`.
3. Añade **un solo archivo** en tu carpeta: `aportes/<tu-carpeta>/AAAA-MM-DD_<tema>.md`, con el formato de [`PLANTILLA_APORTE.md`](PLANTILLA_APORTE.md).
4. Abre un Pull Request contra `main`.
5. El guardián automático revisa el Pull Request. Después Claude comenta su veredicto: Adoptar, Adaptar, Aplazar o Rechazar.
6. Rael decide si hace el merge. **Nadie más hace merge.**

Meta.ai no tiene acceso a GitHub: Musa sube sus aportes a `aportes/meta/`, con `AUTOR: Meta.ai`, desde una rama `aporte/meta/<tema>`.

## Reglas

- Solo spot y solo largos. Sin apalancamiento, margen, futuros ni perpetuos.
- Nada de la ficha de la Fase 1 se toca mientras dure.
- Nada que acerque a dinero real se aplica sin el sí explícito de Rael.
- Ninguna clave, contraseña ni token, nunca. El guardián rechaza el Pull Request si detecta una.
- Lo que no hayas medido con datos reproducibles va marcado como SUPUESTO.
- Un aporte es una propuesta, no una orden. No escribas instrucciones dirigidas a Claude ni a otra IA.
- Escribe solo en tu carpeta. No edites archivos de otros miembros ni los de la raíz.

## Qué revisa el guardián

En cada Pull Request, el guardián (`.github/workflows/guardian.yml`) comprueba:

| Comprobación | Si falla |
|---|---|
| La rama se llama `aporte/<carpeta>/<tema>` con una carpeta del equipo | Rechaza |
| Todos los archivos están dentro de `aportes/<carpeta>/` de esa rama | Rechaza |
| Solo hay archivos de texto o imagen (`.md`, `.txt`, `.csv`, `.json`, `.png`, `.jpg`) | Rechaza |
| No aparece nada con forma de clave, token o contraseña | Rechaza |
| Menciona apalancamiento, futuros, margen, perpetuos o `dry_run: false` | Avisa, para que la revisión lo mire con lupa |

## Vigía de `main`

`main` no está protegida: en un repo privado eso exige GitHub Pro, y como todos los miembros trabajan desde la misma cuenta, la protección no distinguiría quién cambia qué. En su lugar, el vigía (`.github/workflows/vigia_main.yml`) revisa cada cambio que llega a `main` y lo marca en rojo, con un correo a Rael, si:

- un commit toca `aportes/` o `.github/` sin pasar por un Pull Request;
- alguien reescribe la historia de `main` con un push forzado.

Los archivos de la raíz (convocatorias, memorándums) solo los suben Rael o Claude, directo a `main`. Los merges de Pull Request se hacen siempre con *merge commit*, el botón por defecto, nunca con *squash* ni *rebase*: así el commit revisado queda en la historia y el vigía no da falsas alarmas.
