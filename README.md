# strudelP5-tests

La idea de este repositorio es documentar un experimento de integración y sincronización entre strudel y p5.js.

## Instalación local de strudel

1. Lo primero es clonar el respositorio oficial de strudel en local: https://codeberg.org/uzu/strudel/src/branch/main
2. Es necesario instalar pnpm:

``` bash
npm install -g pnpm@latest-10
```

3. Luego instalar las dependecias:

``` bash
pnpm i
```

4. Correr un servidor local para servir el RPEL de strudel:

``` bash
pnpm dev
```

5. Ejecutar el OSCBridge

6. Guardar en la carpeta website/public la aplicación p5.js. En este caso será Visuales visualesHouse.html
7. Servir las visuales visualesHouse.html
8. Pegar en el REPEL de Strudel:

``` js
setcps(0.5)

const pat = s("[bd*2 sd hh oh]").bank("tr909")

$: stack(
  pat.gain('0.05'),
  pat.osc()
)
```

Y también es posible ensayar con este tema:

``` js
setcps(0.5)

// const pat = s("[bd*2 sd hh oh]").bank("tr909")

// $: stack(
//   pat.gain('0.05'),
//   pat.osc()
// )

let bassLine = note("<[c2 c3]*4 [bb1 bb2]*4 [f2 f3]*4 [eb2 eb3]*4>").sound("gm_synth_bass_1")
  .lpf(slider(1000, 0, 1000))

let leadLine = n(`<
[~ 0] 2 [0 2] [~ 2]
[~ 0] 1 [0 1] [~ 1]
[~ 0] 3 [0 3] [~ 3]
[~ 0] 2 [0 2] [~ 2]
>*4`).scale("C4:minor")
.sound("gm_synth_strings_1")

let drumLine = sound("bd*4, [~ <sd cp>]*2, [~ hh]*4")
.bank("tr909")

let hhLine = sound("hh*16").gain(sine)

$: stack(
  bassLine,
  bassLine.osc() // 'gm_synth_bass_1'
)

$: stack(
  leadLine,
  leadLine.osc()
)

$: stack(
  drumLine,
  drumLine.osc()
)

_$: stack(
  hhLine,
  hhLine.osc()
)
```

