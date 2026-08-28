# Handoff: VRZ · Landing page de restauración de faros (Valencia)

## Overview
Landing page de una sola pantalla para VRZ Detallado Automotriz, enfocada
exclusivamente en **restauración de faros a domicilio en Valencia (España)**.
Objetivo único: que el visitante mande una foto del faro por WhatsApp.
Idioma de toda la interfaz: **español de España**. Tono: cercano e informal.

Precio comunicado: **desde 49 € los dos faros**.

## About the Design Files
Los archivos de este paquete son **referencias de diseño hechas en HTML**:
prototipos que muestran el aspecto y el comportamiento buscados, no código de
producción para copiar tal cual. La tarea es **recrear estos diseños en el
entorno del código destino** (React, Vue, Astro, WordPress, etc.) usando sus
patrones y librerías establecidas. Si todavía no hay entorno, elige el
framework más adecuado e impleméntalo ahí.

No hay dos archivos, uno de escritorio y otro de móvil: **es una sola página
responsive**. El "móvil" es la misma página a menos de ~560 px de ancho.

## Fidelity
**Alta fidelidad (hifi).** Colores, tipografías, espaciados e interacciones son
definitivos. Recréalos con precisión.

## Screens / Views

### Vista única: landing (scroll vertical)
Contenedor raíz: fondo #15181C, color de texto #F2F1EE, ancho completo,
`padding-top: env(safe-area-inset-top)`, `padding-bottom: 96px`.
Todas las secciones internas usan `max-width: 1180px; margin: 0 auto` y
padding lateral `clamp(18px, 5vw, 28px)` (+ safe-area izquierda/derecha).

Orden de bloques:

1. **Intro de apertura (overlay, 3 s)** — ver "Interactions".
2. **Header** — barra superior, borde inferior 1px #262B30.
3. **Hero** — titular + comparador de fotos.
4. **Galería de trabajos** (sección 01).
5. **Motivos** (sección 02), fondo #0F1216.
6. **Pasos** (sección 03).
7. **Precio + calculadora** (sección 04), fondo #0F1216.
8. **Vídeo del proceso** (sección 05).
9. **Preguntas frecuentes** (sección 06), fondo #0F1216.
10. **Cierre / contacto** (id `#contacto`).
11. **Footer**.
12. **Barra fija de WhatsApp** — aparece tras 620 px de scroll.

---

#### 2. Header
- `display: flex; align-items: center; justify-content: space-between; gap: 12px; flex-wrap: nowrap`
- Padding: `16px` vertical; lateral `clamp(18px, 5vw, 28px)` + safe-area.
- Izquierda: logotipo `VRZ` (Archivo Black 28px, line-height .8,
  letter-spacing −.025em; "VR" en #FCFCFB, "Z" en #F0912F) + barra diagonal
  ámbar de 4px (`clip-path: polygon(40% 0, 100% 0, 60% 100%, 0 100%)`),
  separador vertical 1×26px #3A9BF0, y descriptor en dos líneas
  "Restauración de faros / Valencia" (Barlow Condensed 600,
  `clamp(11px, 2.7vw, 13px)`, letter-spacing .16em, mayúsculas, #A8AEB4).
- Derecha: enlace **"Contáctanos"** → `#contacto`. Borde 1px #3A9BF0,
  radio 4px, `min-height: 44px`, texto Barlow Condensed 700
  `clamp(13px, 3vw, 14px)`, letter-spacing .14em, mayúsculas, #FCFCFB.
  Hover: fondo #3A9BF0, texto #0F1216.

#### 3. Hero
Grid `repeat(auto-fit, minmax(320px, 1fr))`, gap `clamp(30px, 6vw, 56px)`,
`align-items: center`. Padding vertical `clamp(44px, 9vw, 72px)` arriba.

Columna izquierda (`gap: clamp(18px, 3.4vw, 26px)`):
- Píldora: borde 1px #2E343A, radio 999px, padding 7px 15px, punto ámbar 7px,
  texto "Voy a donde tengas el coche" (Barlow Condensed 600, 13px, .16em).
- H1: Archivo Black `clamp(33px, 6.6vw, 58px)`, line-height 1.04,
  letter-spacing −.02em, #FCFCFB, `text-wrap: balance`.
  Copy: "Tus faros están amarillos. En una hora los dejo como nuevos."
- Párrafo: `clamp(16px, 2.2vw, 19px)`, line-height 1.55, #A8AEB4, max-width 520px.
  Copy: "Restauración de faros a domicilio en Valencia. No hace falta desmontar
  nada ni dejarme el coche: lo hago en la puerta de tu casa y te lo devuelvo listo."
- CTA principal: fondo #F0912F, texto #15181C, radio 5px, padding 17px 24px,
  `flex: 1 1 260px` (ocupa el ancho en móvil), Barlow Condensed 700
  `clamp(17px, 2.4vw, 19px)`, .1em, mayúsculas.
  Copy: "Mándame una foto por WhatsApp". Hover: #FFA648.
- Nota al lado: "Te digo el precio en cinco minutos." 15px #8B9198.
- Tres etiquetas (chips), Barlow Condensed 12px, .12em, radio 4px, padding 7px 11px:
  - "Desde 49 € los dos" — fondo #F0912F, texto #15181C, peso 700.
  - "Una hora de trabajo" y "Sellado UV" — fondo #1D2126, texto #C4C9CD, peso 600.

Columna derecha — **comparador antes/después**:
- Contenedor `aspect-ratio: 4 / 5`, radio 8px, overflow hidden,
  `cursor: ew-resize`, `touch-action: none`, `user-select: none`.
- Dos `<img>` superpuestas a `object-fit: cover`; la de "después" lleva
  `clip-path: inset(0 0 0 R%)` donde R es el estado `reveal` (inicial 52).
- Etiqueta "Antes" arriba izquierda (#A8AEB4) y "Después" arriba derecha
  (#FCFCFB, precedida de una regla ámbar 20×3px), Barlow Condensed 700 13px .24em.
- Manija: línea vertical 2px #F0912F en `left: R%`, y círculo 46px #F0912F
  centrado verticalmente con dos triángulos #15181C (flechas ← →).
- Pie sobre degradado `linear-gradient(to top, rgba(10,12,14,.85), transparent)`:
  "arrastra para comparar" (IBM Plex Mono 11px #C4C9CD).
- Debajo del marco: "Trabajo real, sin retoque: mismo faro, mismo ángulo, misma luz."
  (IBM Plex Mono 12px #767C82).

#### Cabecera de sección (patrón repetido, secciones 01–06)
- Fila: número en Archivo Black 12px #F0912F, regla 26×2px #2E343A,
  rótulo Barlow Condensed 600 13px .24em mayúsculas #8B9198.
- H2: Archivo Black `clamp(26px, 5vw, 36px)`, line-height 1.08,
  letter-spacing −.015em, `text-wrap: balance`.
- Línea de apoyo opcional: `clamp(15px, 2vw, 17px)`, line-height 1.55,
  #8B9198, max-width 560px.
- Separación entre cabecera y contenido: `clamp(28px, 5vw, 40px)`.

#### 4. Galería (01 · Trabajos)
H2 "Antes y después". Apoyo: "Coches reales de esta semana. Toca cada uno para
ver cómo quedó."
Grid `repeat(auto-fit, minmax(260px, 400px))`, `justify-content: start`,
gap `clamp(16px, 3.2vw, 20px)`. **Dos tarjetas**:
1. "BMW Serie 3 · faro izquierdo" — nota "plástico opaco, una hora de trabajo".
2. "Dacia · furgoneta" — nota "faro enmascarado antes de lijar".

Cada tarjeta: marco `aspect-ratio: 4 / 5`, radio 6px; dos `<img>` apiladas
(`object-fit: cover`), la de "después" con `transition: opacity .28s ease` y
opacidad 0/1 según el estado. Etiqueta "ANTES"/"DESPUÉS" arriba izquierda con
`text-shadow: 0 1px 6px rgba(0,0,0,.7)`. Nota al pie sobre degradado.
Debajo: título (Barlow Condensed 700 17px .06em #E9EBEC) y **conmutador
segmentado** "Antes / Después": contenedor fondo #1A1E23, radio 5px, padding 4px;
cada opción `min-height: 44px`, padding lateral 15px, radio 3px,
Barlow Condensed 700 12px .16em; activa = fondo #F0912F, texto #15181C;
inactiva = fondo transparente, texto #8B9198. `transition: background .2s, color .2s`.

#### 5. Motivos (02 · Por qué merece la pena) — fondo #0F1216
H2 "Cinco motivos para no dejarlo pasar".
Grid `repeat(auto-fit, minmax(300px, 1fr))`, gap columna `clamp(24px, 4.6vw, 44px)`.
Cada fila: borde superior 1px #262B30 (la última también inferior),
padding vertical `clamp(18px, 3.4vw, 22px)`, `display: flex`,
gap `clamp(14px, 3vw, 20px)`, `align-items: baseline`.
Marca: regla 18×3px #F0912F con `transform: translateY(-6px)`.
Título: Barlow Condensed 700 `clamp(20px, 3.4vw, 24px)`, .06em, mayúsculas, #FCFCFB.
Texto: 16px, line-height 1.5, #9AA0A6.

Los cinco (título → texto):
1. "Pasas la ITV" → "Un faro opaco te lo pueden marcar como defecto.
   Restaurarlo lo soluciona sin cambiar la pieza."
2. "Vuelves a ver de noche" → "El plástico amarillo se come buena parte de la
   luz que da la bombilla. Con el faro limpio, la carretera se ve."
3. "Cuesta mucho menos que cambiarlo" → "Un faro nuevo de recambio se va a
   varios cientos de euros, más la mano de obra de montarlo."
4. "Listo en una hora" → "No te quedas sin coche ni tienes que dejarlo en
   ningún taller. Lo hago donde esté aparcado."
5. "Vale más cuando lo vendas" → "Los faros amarillos envejecen el coche
   entero. Es lo primero que mira quien va a comprarlo."

#### 6. Pasos (03 · Cómo va)
H2 "Cuatro pasos y ya está". Apoyo: "Desde que me escribes hasta que tienes el
coche listo pasa poco más de una hora."
Grid `repeat(auto-fit, minmax(230px, 1fr))`, gap `clamp(14px, 2.8vw, 18px)`.
Tarjeta: fondo #1A1E23, radio 8px, padding `clamp(22px, 4.4vw, 28px)`
`clamp(20px, 4.2vw, 26px)`, `gap: 13px`.
Numeral Archivo Black 13px #F0912F ("01"…"04"), título Barlow Condensed 700
22px .06em #FCFCFB, texto 16px #9AA0A6.
1. "Me mandas la foto" → "Una foto del faro por WhatsApp, con luz de día. Con eso ya veo el estado."
2. "Te digo precio y día" → "Precio cerrado antes de empezar. Si no te cuadra, no pasa nada."
3. "Voy a tu coche" → "Valencia y alrededores. Basta con que esté aparcado y yo pueda llegar."
4. "Una hora después" → "Faros transparentes y sellados con capa UV. Te enseño el antes y el después."

#### 7. Precio (04) — fondo #0F1216
Grid `repeat(auto-fit, minmax(300px, 1fr))`, gap `clamp(24px, 4.6vw, 44px)`.
- **Bloque de precio**: "Desde" (Barlow Condensed 600 21px .14em #A8AEB4) +
  "49 €" (Archivo Black `clamp(54px, 11vw, 82px)`, line-height .85,
  letter-spacing −.03em, #FCFCFB) + "los dos faros" (Barlow Condensed 700 21px
  .14em #F0912F). Párrafo: "Los dos faros, no uno. El precio final depende de
  cómo esté el plástico: te lo confirmo por WhatsApp con la foto, antes de
  moverme de casa."
- **Tarjeta "Va incluido"**: fondo #1A1E23, radio 8px, padding
  `clamp(24px, 4.6vw, 32px)` `clamp(22px, 4.4vw, 30px)`. Cinco puntos con
  viñeta circular 6px #3A9BF0: lijado progresivo del plástico / pulido hasta
  dejarlo transparente / sellado con capa de protección UV / desplazamiento
  dentro de Valencia / fotos del antes y el después.
- **Calculadora** — `grid-column: 1 / -1`, fondo #1A1E23, borde 1px #2E343A,
  radio 8px, grid interno `repeat(auto-fit, minmax(280px, 1fr))`,
  gap `22px 34px`, `align-items: end`. Contiene:
  - Título "Calcula tu precio" (fila completa).
  - Segmentado "¿Cuántos faros?": Uno / Los dos.
  - Segmentado "¿Cómo están?": Poco / Medio / Muy amarillo.
  - Fila completa: rótulo "Orientativo" + importe en Archivo Black
    `clamp(34px, 8vw, 46px)` #F0912F, y enlace "Confirmar por WhatsApp"
    (borde #3A9BF0, `min-height: 44px`).
  - Nota: "estimación de orientación, no un presupuesto cerrado. dime tus
    importes reales y ajusto la tabla".
  - Segmentados: contenedor fondo #15181C, radio 6px, padding 5px; opción
    `min-height: 44px`, radio 4px; activa fondo #F0912F texto #15181C.

  **Fórmula actual (provisional, a confirmar con el negocio):**
  base = 49 € (los dos) o 35 € (uno); recargo por estado = +0 / +10 / +20 €.

#### 8. Vídeo (05 · El proceso)
H2 "Míralo en un minuto". Marco `aspect-ratio: 16 / 9`, radio 8px, fondo
#1F2429 con trama `repeating-linear-gradient(135deg, #2A2F35 0 2px, transparent 2px 11px)`,
círculo 74px con borde 2px #F0912F y triángulo de play ámbar.
**Marcador**: falta el vídeo real.

#### 9. Preguntas (06 · Dudas) — fondo #0F1216
Contenedor `max-width: 860px`. H2 "Lo que me preguntan siempre".
Apoyo: "Si tu duda no está aquí, mándamela por WhatsApp."
`<details>` con borde superior 1px #262B30 (el último también inferior).
`<summary>`: `min-height: 60px`, padding vertical `clamp(16px, 3.2vw, 20px)`,
`display: flex; justify-content: space-between`; marcador nativo oculto.
Título Barlow Condensed 700 `clamp(19px, 3.2vw, 22px)` .04em mayúsculas #FCFCFB.
Signo "+" 26px #3A9BF0 que rota 45° cuando `[open]` (`transition: transform .18s ease`).
Respuesta: 17px, line-height 1.55, #9AA0A6, max-width 640px.
Las cinco: ¿Hay que desmontar el faro? / ¿Se vuelven a poner amarillos? /
Mi faro está empañado por dentro / ¿A qué zonas te desplazas? / ¿Cómo se paga?
(textos exactos en el HTML).

#### 10. Cierre (#contacto)
H2 "Hazle una foto al faro y mándamela." Archivo Black `clamp(29px, 5.6vw, 44px)`.
Párrafo: "No necesito el modelo, ni la matrícula, ni nada más. Con la foto te
digo el precio y cuándo puedo pasar."
CTA "Abrir WhatsApp" (mismos estilos que el CTA del hero).
Tarjeta de contacto: fondo #1A1E23, radio 8px; avatar circular 54px #15181C con
la "V" + barra ámbar; nombre "VRZ Detallado Automotriz"; "Estilo & Protección";
y una lista en IBM Plex Mono 14px con etiquetas de 78px:
whatsapp / instagram / zona / horario.

**DATOS PENDIENTES (hoy son marcadores):**
- teléfono: `+34 000 000 000`
- instagram: `@usuario`
- zona: "Valencia y área metropolitana"
- horario: "Lunes a sábado"
El CTA apunta a `#contacto`; **hay que cambiarlo por**
`https://wa.me/34XXXXXXXXX?text=...` cuando exista el número.

#### 11. Footer
Borde superior 1px #262B30, padding `clamp(26px, 5vw, 34px)` lateral.
Logo pequeño + "Restauración de faros · Valencia" + "Estilo & Protección".

#### 12. Barra fija de WhatsApp
`position: fixed; bottom: 0; z-index: 30`, fondo #1A1E23, borde superior
1px #2E343A, `box-shadow: 0 -14px 34px rgba(0,0,0,.45)`,
padding `12px clamp(14px, 4vw, 22px)` + `env(safe-area-inset-bottom)`,
`flex-wrap: nowrap`.
Izquierda: logo VRZ 19px + "Faros desde 49 € / los dos" (dos líneas,
`clamp(11px, 2.9vw, 14px)`). Derecha: CTA "Mándame la foto" fondo #F0912F,
`min-height: 44px`, `white-space: nowrap`.

## Interactions & Behavior

### Intro de apertura (3 s en total)
Overlay `position: fixed; inset: 0; z-index: 100`, fondo #000, centrado.
Se desmonta a los 3000 ms.
1. **Caída en píxeles** — el símbolo (la letra "V" en #FCFCFB + la barra
   diagonal en #F0912F) se dibuja como una malla de cuadrados absolutos.
   Rejilla de 11 filas × 16 columnas; lado del cuadrado **25 px** en escritorio
   y **16 px** por debajo de 560 px de ancho; el cuadrado pintado mide
   `lado − 3 px`. Cada cuadrado cae con
   `@keyframes pxDrop` (`translateY(-72vh) scale(.55)` opacidad 0 →
   `translateY(0) scale(1)` opacidad 1), duración .62 s,
   `cubic-bezier(.22, 1.5, .36, 1)`, retardo `col*0.026 + row*0.022` s.
2. **Rebote** — a los 1.22 s el conjunto ejecuta `@keyframes logoHit`
   (.8 s, `cubic-bezier(.3, 0, .2, 1)`): squash a `scale(1.09, .84)` con
   `translateY(14px)`, rebote a `translateY(-30px) scale(.96, 1.07)`,
   segundo bote menor, y reposo.
3. **Texto** — a los 1.76 s entra la regla azul 220×3px y
   "Restauración de faros · Valencia" con `@keyframes wordIn`
   (opacidad 0→1, `translateY(16px)`→0, .6 s).
4. **Salida** — a los 2.34 s el overlay ejecuta `@keyframes ovOut`
   (opacidad 1→0, `scale(1)`→`scale(1.14)`, .62 s,
   `cubic-bezier(.4, 0, .2, 1)`).
Existe un flag `intro` para desactivarla.

### Revelado por scroll
Cada `section`, `header` y `footer` hijo directo de la raíz arranca en
`opacity: 0; transform: translateY(30px)` con
`transition: opacity .75s cubic-bezier(.2,.8,.2,1), transform .75s (idem)`.
Un `IntersectionObserver` (`rootMargin: '0px 0px -12% 0px'`, `threshold: .06`)
los pone a `opacity: 1; translateY(0)` y deja de observarlos.
El observador se instala a los **2250 ms** si la intro está activa, o a los
**60 ms** si no.

### Comparador del hero
Eventos de **puntero** (`pointerdown` / `pointermove` / `pointerup` /
`pointercancel`), con `setPointerCapture`. Al arrastrar se calcula
`(clientX − rect.left) / rect.width * 100` y se limita a **2–98 %**.
Solo se mueve con el botón/dedo pulsado.

### Galería
Cada tarjeta guarda su propio estado `'antes' | 'despues'`; el conmutador
cambia la opacidad de la imagen superior. Independiente por tarjeta.

### Calculadora
Estados `faros` (1 | 2) y `estado` (0 | 1 | 2). Importe recalculado al instante.

### Barra fija
Aparece cuando `window.scrollY > 620`; listener de scroll pasivo.

### Preguntas
`<details>/<summary>` nativos. El "+" gira 45° con `[open]`.

### Áreas de toque
**Todos** los elementos interactivos tienen `min-height: 44px`. Mantenlo.

## State Management
- `reveal: number` — posición del comparador en % (inicial 52).
- `intro: boolean` — overlay de apertura visible (inicial true).
- `sticky: boolean` — barra fija visible (inicial false).
- `gal: ('antes'|'despues')[]` — una entrada por tarjeta de galería (2).
- `faros: 1 | 2` — inicial 2.
- `estado: 0 | 1 | 2` — inicial 1.
Sin peticiones de red. Sin datos externos.

## Design Tokens

### Colores
| Uso | Hex |
|---|---|
| Fondo base / grafito | #15181C |
| Fondo de sección alterna | #0F1216 |
| Fondo de tarjeta | #1A1E23 |
| Fondo de chip / tarjeta secundaria | #1D2126 |
| Marcador de foto (trama base) | #1F2429 / #22272C |
| Trama de marcador (líneas) | #2A2F35 / #2E343A |
| Borde sutil | #262B30 |
| Borde de tarjeta | #2E343A |
| Azul VRZ (acento estructural) | #3A9BF0 |
| Azul hover | #6FB6F5 |
| Ámbar VRZ (acento de acción) | #F0912F |
| Ámbar hover | #FFA648 |
| Texto principal | #F2F1EE |
| Texto alto contraste / logo | #FCFCFB |
| Texto secundario | #C4C9CD / #A8AEB4 |
| Texto terciario | #9AA0A6 / #8B9198 |
| Texto mono / notas | #767C82 |

Regla de marca: **un acento por pieza**. El azul es estructural (reglas,
bordes, viñetas); el ámbar marca acción y estado activo.

### Tipografía (Google Fonts, licencia abierta)
- **Archivo Black** — logotipo, H1/H2, cifras destacadas. letter-spacing
  −.015em a −.03em.
- **Barlow Condensed** 500/600/700 — rótulos, botones, títulos de tarjeta.
  Siempre mayúsculas con letter-spacing abierto (.04em–.44em) y el mismo valor
  replicado en `padding-left` para compensar el espaciado final.
- **Barlow** 400/500/600 — texto corrido.
- **IBM Plex Mono** 400 — notas técnicas, datos de contacto, pies de foto.

### Escala tipográfica
H1 `clamp(33px, 6.6vw, 58px)` · H2 `clamp(26px, 5vw, 36px)` ·
H2 de cierre `clamp(29px, 5.6vw, 44px)` · entradilla `clamp(16px, 2.2vw, 19px)` ·
apoyo de sección `clamp(15px, 2vw, 17px)` · cuerpo 16–17px ·
título de tarjeta 22–24px · rótulo 13px · nota mono 11–12px.

### Espaciado
- Padding lateral de página: `clamp(18px, 5vw, 28px)` + safe-area.
- Padding vertical de sección: `clamp(48px, 9vw, 72px)`; cierre
  `clamp(56px, 10vw, 84px)`; hero `clamp(44px, 9vw, 72px)`.
- Cabecera → contenido: `clamp(28px, 5vw, 40px)`.
- Rejillas de tarjetas: `clamp(14px, 2.8vw, 20px)`.
- Padding de tarjeta: `clamp(22px, 4.6vw, 32px)` / `clamp(20px, 4.4vw, 30px)`.

### Radios
Página/tarjeta 8px · marco de galería 6px · botón 4–5px · píldora 999px ·
opción de segmentado 3–4px.

### Sombras
Solo una: la barra fija, `0 -14px 34px rgba(0,0,0,.45)`.
**Prohibido** añadir sombras, brillos o degradados a la marca.

### Rejillas responsive
Hero `minmax(320px, 1fr)` · galería `minmax(260px, 400px)` con
`justify-content: start` · motivos y precio `minmax(300px, 1fr)` ·
pasos `minmax(230px, 1fr)` · calculadora interna `minmax(280px, 1fr)`.
No hay media queries: todo el responsive es `clamp()` + `auto-fit`.

### Área segura (iOS)
Raíz: `padding-top: env(safe-area-inset-top)`.
Header: laterales `+ env(safe-area-inset-left/right)`.
Barra fija: `padding-bottom: calc(12px + env(safe-area-inset-bottom))`.

## Assets
En `fotos/` (fotos reales del taller, aportadas por el cliente, 1536×2048):
- `faro-antes.png` / `faro-despues.png` — BMW Serie 3, faro izquierdo.
- `furgo-antes.png` / `furgo-despues.png` — furgoneta Dacia.

Marca (en `marca/`): `vrz-logo-principal.svg/.png`,
`vrz-logo-horizontal.svg/.png`, `vrz-simbolo.svg/.png`,
`vrz-una-tinta-blanco.svg/.png`. Los SVG llevan **texto vivo**: hay que
convertirlo a curvas (con Archivo Black instalada) antes de imprimir o cortar.

El logotipo de la página **no usa imágenes**: se compone con tipografía + un
`clip-path` para la barra diagonal. Mantenlo así (escala perfecta, sin peso).

Pendiente: el vídeo del proceso (marcador 16:9) y un tercer par antes/después
si se quiere ampliar la galería.

## Files
- `vrz-faros-lp.html` — **la página, autocontenida**: fuentes y fotos
  incrustadas, abre sin servidor y sin internet. Es la referencia visual
  definitiva; ábrela en el navegador y compárala mientras implementas.
- `fotos/` — las cuatro fotos originales a resolución completa.
- `marca/` — logotipos en SVG y PNG para favicon, cabecera y compartir.
- `README.md` — este documento.

## Notas de implementación
1. **Un solo layout responsive.** No construyas una versión de escritorio y
   otra de móvil: es la misma página con `clamp()` y `auto-fit`.
2. **El WhatsApp es el producto.** Todos los CTA deben acabar en un enlace
   `https://wa.me/…` con texto prerrellenado. Hoy apuntan a `#contacto`.
3. **La calculadora es orientativa.** Los importes hay que confirmarlos con el
   negocio antes de publicar; deja los números en un único objeto de
   configuración, no repartidos por el marcado.
4. **Respeta los 44 px** de área de toque en todo lo interactivo.
5. **La intro debe poder desactivarse** y no debe bloquear el contenido si el
   JavaScript falla: la página tiene que quedar visible igualmente
   (hoy el revelado por scroll también depende de JS — considera envolver esa
   mejora en un chequeo de `prefers-reduced-motion` y un fallback visible).
6. **Idioma:** español de España en toda la interfaz.
