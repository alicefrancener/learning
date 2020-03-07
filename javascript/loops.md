# Loops

As três principais informações que qualquer loop deve conter são:

1. **Quando começar:** o código que dá início ao loop — definindo o valor inicial de uma variável por exemplo.
2. **Quando parar:** a condição lógica para testar se o loop deve continuar.
3. **Como ir para o próximo item:** a etapa de incremento ou decremento

## Loop while

```js
var start = 0; // quando começar
while (start < 10) { // quando parar
  console.log(start);
  start = start + 2; // como ir para o próximo item
}
```

## Loop for

```js
for (var i = 0; i < 6; i = i + 1) {
  console.log("Printing out i = " + i);
}
```

## Incremento e decremento

```js
x++ or ++x // same as x = x + 1
x-- or --x // same as x = x - 1
x += 3 // same as x = x + 3
x -= 6 // same as x = x - 6
x *= 2 // same as x = x * 2
x /= 5 // same as x = x / 5
```

---

Notas de estudos do curso [Intro to Javascript](https://www.udacity.com/course/intro-to-javascript--ud803) da [Udacity](https://www.udacity.com).