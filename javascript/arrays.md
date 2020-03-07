
# Arrays
- [Arrays](#arrays)
  - [Índice de uma array](#%c3%8dndice-de-uma-array)
  - [Métodos e propriedades de arrays](#m%c3%a9todos-e-propriedades-de-arrays)
    - [Length](#length)
    - [Push](#push)
    - [Pop](#pop)
    - [Splice](#splice)
    - [Outros métodos](#outros-m%c3%a9todos)
  - [Loop de repetição forEach](#loop-de-repeti%c3%a7%c3%a3o-foreach)
  - [Map](#map)
  - [Arrays em arrays](#arrays-em-arrays)

Um array é útil pois armazena **múltiplos valores** em uma única e organizada estrutura de dados.

```js
var donuts = ["glazed", "powdered", "jelly"];
var mixedData = ["abcd", 1, true, undefined, null, "all the things"];
```

Você pode mesmo armazenar um array dentro de outra, criando um array aninhada! Arrays aninhadas podem ser particularmente difíceis de ler, então, é comum escrevê-las em uma linha, usando uma nova linha após cada vírgula:

```js
// cria uma array `arraysInArrays`, composta de três arrays
var arraysInArrays = [
  [1, 2, 3],
  ["Julia", "James"],
  [true, false, true, false]
];
```

## Índice de uma array

Os elementos de uma array são indexados começando na posição `0`. Se você tentar acessar um elemento em um índice que não existe, um valor de indefinido será retornado.

```js
var donuts = ["glazed", "powdered", "sprinkled"];
console.log(donuts[0]);
console.log(donuts[3]);
```

> *Returns:*  
> "glazed"  
> `undefined`

JavaScript fornece um grande número de métodos embutidos para modificar arrays e acessar valores dentro dela. Ver documentação [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

## Métodos e propriedades de arrays

### Length

Você pode descobrir o tamanho do array usando a propriedade `length`.

```js
var donuts = ["glazed", "powdered", "sprinkled"];
console.log(donuts.length);
```

### Push 

O método `push()` adiciona elementos ao fim de um array. O método `push()` retorna o tamanho da array após um elemento ser adicionado.

```js
var donuts = ["glazed", "powdered", "sprinkled"];
donuts.push("powdered"); // mover "powdered" para o fim da array `donuts`
```

> *Returns*: 4

### Pop

O método `pop()` remove elementos do fim de um array. `pop()` também retorna o elemento que foi removido, no caso de você precisar usá-lo.

```js
var donuts = ["glazed", "powdered", "sprinkled"];
donuts.pop();
```

> *Returns*: "sprinkled"

### Splice

`splice()` é um outro método acessível que permite que você adicione e remova elementos de qualquer lugar dentro de uma array.

O primeiro argumento representa o índice inicial de onde você quer alterar a array, o segundo argumento representa o número de elementos que você quer remover e o restante dos argumentos representam os elementos que você quer adicionar.

```js
var months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// inserts at 1st index position
console.log(months);
// expected output: Array ['Jan', 'Feb', 'March', 'April', 'June']

months.splice(4, 1, 'May');
// replaces 1 element at 4th index
console.log(months);
// expected output: Array ['Jan', 'Feb', 'March', 'April', 'May']
```

### Outros métodos

Métodos descritos em [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

* `reverse()` method reverses an array in place
* `sort()` method sorts the elements of an array in place and returns the array.
* `shift()` method removes the first element from an array and returns that removed element
* `slice()` method returns a shallow copy of a portion of an array into a new array object selected from `begin` to `end` (`end` not included).
* `join()` method creates and returns a new string by concatenating all of the elements in an array (or an array-like object), separated by commas or a specified separator string.
* `concat()` method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.

## Loop de repetição forEach

O método `forEach()` dá uma alternativa para iterar sobre uma array e manipular cada elemento da array com uma expressão em função inline.

```js
var donuts = ["jelly donut", "chocolate donut", "glazed donut"];

donuts.forEach(function(donut) {
  donut += " hole";
  donut = donut.toUpperCase();
  console.log(donut);
});
```

> *Returns*:  
JELLY DONUT HOLE  
CHOCOLATE DONUT HOLE  
GLAZED DONUT HOLE  

O método `forEach()` itera sobre a array sem a necessidade de índice explicitamente definida. No exemplo acima, `donut` corresponde ao elemento na própria array. Isso é diferente de um loop de repetição `for` ou `while` onde um índice é usado para acessar cada elemento de uma array:

```js
for (var i = 0; i < donuts.length; i++) {
  donuts[i] += " hole";
  donuts[i] = donuts[i].toUpperCase();
  console.log(donuts[i]);
}
```

## Map

Usar `forEach()` não será útil se você quiser modificar permanentemente a array original. forEach() sempre retorna `undefined`. Contudo, criar uma nova array a partir de uma array existente é simples, com o poderoso método `map()`.

Com o método `map()`, você pode utilizar uma array, realizar algumas operações sobre cada elemento dela e retornar uma nova.

```js
var donuts = ["jelly donut", "chocolate donut", "glazed donut"]
var improvedDonuts = donuts.map(function(donut) {
  donut += " hole";
  donut = donut.toUpperCase();
  return donut;
});
```

> *Returns*:  
donuts array: ["jelly donut", "chocolate donut", "glazed donut"]  
improvedDonuts array: ["JELLY DONUT HOLE", "CHOCOLATE DONUT HOLE", "GLAZED DONUT HOLE"]

## Arrays em arrays

Exemplo de array de arrays, que possui o nome de cada donut associado à sua posição em uma caixa.

```js
var donutBox = [
  ["glazed", "chocolate glazed", "cinnamon"],
  ["powdered", "sprinkled", "glazed cruller"],
  ["chocolate cruller", "Boston creme", "creme de leche"]
];
```

Se você quisesse fazer um loop sobre a caixa de donut e exibir cada donut (juntamente à sua posição na caixa), iniciaria escrevendo um loop de repetição `for` para fazer o loop em cada linha da caixa de donuts. Uma vez que cada linha é uma array de donuts, você, então, precisa definir um loop de repetição interno para fazer o loop sobre cada célula nas arrays.

```js
for (var row = 0; row < donutBox.length; row++) {
  // aqui, donutBox[row].length se refere ao tamanho do array de donut sendo percorrido atualmente
  for (var column = 0; column < donutBox[row].length; column++) {
    console.log(donutBox[row][column]);
  }
}
```

***

Notas de estudos do curso [Intro to Javascript](https://www.udacity.com/course/intro-to-javascript--ud803) da [Udacity](https://www.udacity.com).