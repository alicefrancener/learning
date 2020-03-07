# Funções

Funções permitem o empacotamento de linhas de código que você pode utilizar (e constantemente reutilizar) em seus programas.
- [Funções](#fun%c3%a7%c3%b5es)
  - [Declarando funções](#declarando-fun%c3%a7%c3%b5es)
  - [Parâmetros x argumentos](#par%c3%a2metros-x-argumentos)
  - [`return` x `log`](#return-x-log)
  - [Escopo](#escopo)
    - [Conflito](#conflito)
    - [Resumo escopo](#resumo-escopo)
  - [Hoisting](#hoisting)
    - [Resumo hoisting](#resumo-hoisting)
  - [Function expression](#function-expression)
    - [Expressões de função e hoisting](#express%c3%b5es-de-fun%c3%a7%c3%a3o-e-hoisting)
  - [Padrões com expressões de funções](#padr%c3%b5es-com-express%c3%b5es-de-fun%c3%a7%c3%b5es)
    - [Funções como parâmetros](#fun%c3%a7%c3%b5es-como-par%c3%a2metros)
    - [Expressões de função inline](#express%c3%b5es-de-fun%c3%a7%c3%a3o-inline)
    - [Por que utilizar expressões anônimas de função inline?](#por-que-utilizar-express%c3%b5es-an%c3%b4nimas-de-fun%c3%a7%c3%a3o-inline)

## Declarando funções

* Parâmetro: funções podem ou não conter parâmetros, que são separados por vírgulas
* `return`: funções podem ou não conter o comando `return`. Se não tiver o comando, o console retornará `undefined`. `undefined` é o valor padrão de retorno do console quando nada está explicitamente sendo retornado com o uso da palavra-chave especial `return`.

```js
//função com dois parâmetros
function doubleGreeting(name, otherName) {
  // código para cumprimentar duas pessoas!
}
```

```js
//função sem parâmetro que retornará undefined quando invocada
function sayHello() {
  var message = "Hello!";
  console.log(message);
}

sayHello();
```

> *Returns:*  
> "Hello!"  
> `undefined`

Agora, para que sua função faça alguma coisa, você deve **invocar** ou **chamar** a função utilizando seu nome, seguido de parênteses, com os argumentos que são passados a ela.

## Parâmetros x argumentos

Em uma primeira abordagem, pode ser um pouco difícil saber quando algo é um parâmetro ou um argumento. A diferença principal está em onde eles aparecem no código. Um **parâmetro** sempre será um **nome de uma variável**, e ele aparece na **declaração da função**. Por outro lado, um **argumento** sempre será um **valor** (ou seja, qualquer um dos tipos de dados do JavaScript - do tipo number, string, boolean, etc.) e sempre aparecerá no código quando a **função é chamada ou invocada**.

```js
// x e y são parâmetros nesta declaração de função
function add(x, y) {
  // corpo da função
  var sum = x + y;
  return sum; // comando return
}

// 1 e 2 são passados para a função como argumentos
var sum = add(1, 2); // invocando a função
```

## `return` x `log`

* `console.log()`: use to **print** a valur to the JavaScript console  
* `return`: use to **stop** execution of a function and **return** a value back to the caller

## Escopo

* **global scope:** identifiers can be acessed everywhere within ypur program
* **function scope:** identifiers can be acessed everywhere inside the function it was defined in

### Conflito

Abaixo, a variável global `bookTitle`tem sem valor reatribuído (reassigned) para o valor contido dentro da função. 

```js
var bookTitle = "Le Petit Prince";
console.log(bookTitle);

function displayBookEnglish(){
  bookTitle = "The Little Prince";
  console.log(bookTitle);
}

displayBookEnglish();
console.log(bookTitle);
```

> *Returns:*  
> "Le Petit Prince"  
> "The Little Prince"  
> "The Little Prince"

Para evitar isso, é preciso declarar uma nova variável dentro da função:

```js
var bookTitle = "Le Petit Prince";
console.log(bookTitle);

function displayBookEnglish(){
  var bookTitle = "The Little Prince"; //nova variável
  console.log(bookTitle);
}

displayBookEnglish();
console.log(bookTitle);
```

> *Returns:*  
> "Le Petit Prince"  
> "The Little Prince"  
> "Le Petit Prince"

### Resumo escopo

* Se um indentificador é declarado em escopo global, ele estará disponível em qualquer lugar.
* Se um identificador é declarado em um escopo de função, ele estará disponível na função em que foi declarado (mesmo em funções declaradas dentro de outra função).
* Ao tentar acessar um identificador, o mecanismo do JavaScript primeiramente olhará a função atual. Se ele não achar nada, continuará na próxima função em camada mais externa, para ver se consegue encontrar o identificador. Isso continuará sendo feito até que ele alcance o escopo global.
* Identificadores globais são uma má idéia. Eles podem levar a nomes ruins para variáveis, conflito de nomes de variáveis e código confuso

## Hoisting

* **hoisting**: before any JavaScript is executed, all function declarations are "hoisted" to the top of their current scope

*hoist: içar, levantar*

Quando o código está sendo interpretado, a declação das funções é elevada ao topo. Hoisting também ocorre com declações de variáveis dentro das funções, porém somente as declarações, não as atribuições.

Abaixo, exemplo de hoisting da função e de variável dentro da função:

```js
sayHi("Julia");

function sayHi(name) {
  console.log(greeting + " " + name);
  var greeting;
}
```

> *Returns:*  
> `undefined` Julia  

O `undefined` é devido à variável greeting

Abaixo, exemplo de hoisting da função e da declaração da variável dentro da função (porém, não ocorre hoisting da atribuição da variável greeting):

```js
sayHi("Julia");

function sayHi(name) {
  console.log(greeting + " " + name);
  var greeting = "Hello";
}
```

> *Returns:*  
> `undefined` Julia  

A declaração da variável é feita no topo do escopo atual (o topo da função). Lembre-se que a declaração é feita, não a atribuição.

Para **evitar erros como esses** as funções devem ser declaras no topo dos scripts e as variáveis devem ser declaradas no topo das funções, como abaixo:

```js
function sayHi(name) {
  var greeting = "Hello";
  console.log(greeting + " " + name);
}

sayHi("Julia");
```

> *Returns:*  
> Hello Julia  

### Resumo hoisting

* O JavaScript iça (hoists) declarações de função e declarações de variável até o topo do escopo atual.
* Atribuições de variáveis não são içadas (hoisted).
* Declare funções e variáveis no topo de seus scripts, então, a sintaxe e o comportamento serão consistentes um com o outro.

## Function expression

Quando uma função é armazenada dentro de uma variável, ela é chamada de expressão de função (**function expression**).

Duas formas de definir função em JavaScript:

* Function declation

```js
function catSays(max) {
  // code here
}

catSays();
```

* Function expression

```js
var catSays = function (max) {
  // code here
};

catSays();
```

Acima, a função é anônima, uma função sem nome, e você a armazenou em uma variável chamada `catSays`. E, se você tentar acessar o valor da variável `catSays`, verá a função sendo retornada de volta para você.

```js
catSays;
```

> *Returns:*  
> function(max) {  
> &nbsp;&nbsp;&nbsp;&nbsp;//code here  
> };

### Expressões de função e hoisting

Todas as *declarações de funções são içadas (hoisted)* e carregadas antes de o script ser realmente rodado. *Expressões de função não são içadas (hoisted)*, uma vez que elas envolvem atribuição de variável e somente declarações de variáveis são içadas (hoisted). A expressão de função não será carregada até que o interpretador chegue a ela no script.

## Padrões com expressões de funções

### Funções como parâmetros

Ter a possibilidade de armazenar uma função em uma variável torna realmente simples passar uma função para outra. Uma função que é passada para outra é chamada de **callback**.

Vamos supor que você tenha uma função `helloCat()` e queira que ela retorne "Hello", seguido de uma string de "meows", como você tinha com a `catSays`. Bem, em vez de refazer todo o trabalho duro, você pode fazer a `helloCat()` aceitar uma função callback e passar a `catSays`.

```js
// expressão de função catSays
var catSays = function(max) {
  var catMessage = "";
  for (var i = 0; i < max; i++) {
    catMessage += "meow ";
  }
  return catMessage;
};

// declaração de função helloCat aceitando um callback
function helloCat(callbackFunc) {
  return "Hello " + callbackFunc(3);
}

// passa catSays como função callback
helloCat(catSays);
```

### Expressões de função inline

Uma expressão de função é quando uma função é atribuída a uma variável. Em JavaScript, isso também pode acontecer quando você passa uma função inline como um argumento para outra função. Tome o exemplo `favoriteMovie` como referência:

```js
// Expressão de função que atribui a função displayFavorite 
// à variável favoriteMovie
var favoriteMovie = function displayFavorite(movieName) {
  console.log("My favorite movie is " + movieName);
};

// Declaração de função que possui dois parâmetros: uma função para exibir
// uma mensagem, juntamente ao nome de um filme
function movies(messageFunction, name) {
  messageFunction(name);
}

// Chama a função movies, passa a função favoriteMovie e o nome do filme
movies(favoriteMovie, "Finding Nemo");
```

> *Returns:* My favorite movie is Finding Nemo

Mas você poderia ter contornado a primeira atribuição da função, passando a função para a função inline `movies()`.

```js
// Declaração de função que recebe dois argumentos: uma função para exibir
// uma mensagem, juntamente ao nome de um filme
function movies(messageFunction, name) {
  messageFunction(name);
}

// Chama a função movies, passa a função e o nome do filme
movies(function displayFavorite(movieName) {
  console.log("My favorite movie is " + movieName);
}, "Finding Nemo");
```

> *Returns:* My favorite movie is Finding Nemo

Esse tipo de sintaxe, escrevendo expressões de função que passam uma função para outra **inline**, é bem comum em JavaScript.

### Por que utilizar expressões anônimas de função inline?

Utilizar uma expressão anônima de função inline pode parecer como uma coisa não muito útil de início. Por que definir uma função que pode somente ser utilizada uma única vez e que você não pode nem chamar pelo nome?

Expressões anônimas de função inline são geralmente utilizadas com callbacks de funções que provavelmente não serão reutilizadas em outro lugar. Sim, você poderia armazenar a função em uma variável, dar um nome a ela e passá-la como você viu nos exemplos acima. No entanto, quando já é de seu conhecimento que a função não será reutilizada, defini-la inline pode economizar muitas linhas de código.

---

Notas de estudos do curso [Intro to Javascript](https://www.udacity.com/course/intro-to-javascript--ud803) da [Udacity](https://www.udacity.com).