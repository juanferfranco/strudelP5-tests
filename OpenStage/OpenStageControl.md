# Unidad 3 actividad 3

<img width="1919" height="551" alt="image" src="https://github.com/user-attachments/assets/8febfbcf-6fe9-406d-b9c5-4d8c22b00966" />

El archivo OSCUI.json tiene las visuales de la superficie de control

> [!NOTE]
> Es importante notar dos cosas: se cambió el puerto del servidor web del 8080 (default) al 8086 porque el puerto 8080 lo tiene ocupado strudel
> El puerto udp se configuró en el 9000 porque el bridge está escuchando aquí.

**Strudel Test**

Para las pruebas con las visuales

```js
setcps(0.5)

//const pat = s("[bd*2 sd hh oh]").bank("tr909")

// const pat = s("[bd*2]").bank("tr909")

const pat = s("bd*4 sd hh*8 oh").bank("tr909")

// const pat = s("bd*4 sd sd mt").bank("tr909")

// const pat = s("cr").bank("tr909")

$: stack(
  pat.gain('0.5'),
  pat.osc()
)
```
