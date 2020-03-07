# Objetos
- [Objetos](#objetos)
  - [Objetos literais](#objetos-literais)
  - [Métodos](#m%c3%a9todos)
  - [Convenções de nomenclatura](#conven%c3%a7%c3%b5es-de-nomenclatura)
  - [Acessar métodos e propriedades](#acessar-m%c3%a9todos-e-propriedades)

* Primitive Data Types: strings, numbers, booleans, undefined, null
* Objects: estrutura de dados

Obs: `typeof` é um operador que retorna o nome do tipo de dado que o segue

```js
typeof "hello" // retorna "string"
typeof true // retorna "boolean"
typeof [1, 2, 3] // retorna "object" (Arrays são do tipo object)
typeof function hello() { } // retorna "function"
```

## Objetos literais

```js
var sister = {
  name: "Sarah", 
  age: 23,
  parents: [ "alice", "andy" ],
  siblings: ["julia"],
  favoriteColor: "purple",
  pets: true
};
```

A sintaxe acima é chamada **notação literal de objeto**. Há algumas coisas importantes de que você precisa se lembrar quando está estruturando um objeto literal:

* A "chave" (representando o nome da **propriedade** ou **método**) e seu "valor" são separados de cada um por **dois pontos**
* Os pares `chave: valor` são separados de cada um por **vírgulas**
* O objeto inteiro é colocado dentro de chaves `{ }`.

Exemplos de como você pode recuperar informações sobre o objeto criado por você.

```js
// duas maneiras equivalentes de usar a chave para retornar seu valor
sister["parents"] // retorna [ "alice", "andy" ]
sister.parents // também retorna ["alice", "andy"]
```

O uso de `sister["parents"]` é chamado de **notação de colchetes** (por causa dos colchetes) e o uso de `sister.parents` é chamado de **notação de ponto** (por causa do ponto).

## Métodos

O objeto irmã acima contém um bocado de propriedades sobre minha irmã, mas não diz realmente o que minha irmã faz. Por exemplo, digamos que minha irmã gostar de pintar. Você pode ter um método `paintPicture`() que retorna "Sarah paints a picture!" toda vez que chamá-lo. A sintaxe para isso é muito semelhante a como você definiu as propriedades do objeto. A única diferença é que o valor no par chave:valor será uma função.

```js
var sister = {
  name: "Sarah",
  age: 23,
  parents: [ "alice", "andy" ],
  siblings: ["julia"],
  favoriteColor: "purple",
  pets: true,
  paintPicture: function() { return "Sarah paints!"; }
};

sister.paintPicture(); //retorna: "Sarah paints!"
```

## Convenções de nomenclatura

* Não usar números como o primeiro caracter no nome de propriedades (ex: `1stChild`)
* Não usar espaços e hifen nos nomes das propriedades
* Usar **camel case** para propriedades com múltiplos nomes (ex: ao invés de usar `fire-truck` usar `fireTruck`);

## Acessar métodos e propriedades

```js
var myObj = {
  color: "orange",
  shape: "sphere",
  type: "food",
  eat: function() { return "yummy" }
};

myObj.eat(); // método
myObj.color; // propriedade
```

***

Notas de estudos do curso [Intro to Javascript](https://www.udacity.com/course/intro-to-javascript--ud803) da [Udacity](https://www.udacity.com).