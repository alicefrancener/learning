# Tipos de dados e variáveis

- [Tipos de dados e variáveis](#tipos-de-dados-e-vari%c3%a1veis)
  - [JavaScript Data Types](#javascript-data-types)
  - [Operadores](#operadores)
  - [Comentários](#coment%c3%a1rios)
  - [Strings](#strings)
  - [Concatenação de strings](#concatena%c3%a7%c3%a3o-de-strings)
  - [Variáveis](#vari%c3%a1veis)
  - [Índice de string](#%c3%8dndice-de-string)
  - [Fazendo o "escape" de strings](#fazendo-o-%22escape%22-de-strings)
  - [Caracteres especiais](#caracteres-especiais)
  - [Comparando strings](#comparando-strings)
  - [Booleanos](#booleanos)
    - [true | false](#true--false)
  - [null, undefined and NaN](#null-undefined-and-nan)
  - [Igualdade](#igualdade)
    - [Coerção de tipo implícita](#coer%c3%a7%c3%a3o-de-tipo-impl%c3%adcita)
    - [Igualdade estrita](#igualdade-estrita)

## JavaScript Data Types

- numbers
- strings
- booleans
- null
- undefined

## Operadores

| Operador | Significado          |
| -------- | -------------------- |
| <        | menor que            |
| >        | maior que            |
| <=       | menor que ou igual a |
| >=       | maior que ou igual a |
| ==       | igual a              |
| !=       | diferente de         |

## Comentários

```js
// uma linha de comentário
```

```js
/*
 * Bloco de comentário
 * em JavaScript
 */
```

## Strings

É correto utilizar aspas duplas " ou simples ' com strings, desde que você mantenha a consistência.

## Concatenação de strings

```js
"Hello," + " World";
```

```js
"Hello," + 5 * 10;
```

> _Returns: "Hello50"_

Transforma o número (50) em uma string **(coerção de tipo implícita)**.

## Variáveis

Creating a Variable in JavaScript: _var variableName = value_

```js
var greeting = "Hello";
```

Convenções de nomenclatura para variávels: camelCase  
[Guia de Estilo JavaScript do Google](https://google.github.io/styleguide/jsguide.html)

## Índice de string

Caracters em uma string são indexados começando pelo 0

```js
"James"[0];
```

> _Returns: "J"_

```js
var name = "James";
name[0];
```

> _Returns: "J"_

De maneira alternativa, pode-se usar o método `charAt()` para acessar caracteres individuais. Por exemplo, `name.charAt(0)` para retornar a letra acima.

## Fazendo o "escape" de strings

Em JavaScript, você utiliza a barra invertida para fazer o escape de outros caracteres.

Fazer o escape um caractere significa dizer ao JavaScript para ignorar o significado especial do caractere e somente utilizar seu valor literal. Isso é útil para caracteres que possuem significados especiais, como aspas "…"

```js
"The man whispered, \"please speak to me.\"";
```

> _Returns: The man whispered, "please speak to me."_

## Caracteres especiais

Aspas não são os únicos caracteres especiais que precisam de escape. Uma pequena amostra de alguns caracteres especiais comumente utilizados em JavaScript.

| Código | Caractere           |
| ------ | ------------------- |
| \\\    | \ (barra invertida) |
| \\"    | " (aspas duplas)    |
| \\'    | ' (aspas simples)   |
| \\n    | nova linha          |
| \\t    | tab                 |

## Comparando strings

Ao se comparar strings a identificação de letras minúsculas e maiúsculas importa

```js
"Yes" == "yes";
```

> _Returns: false_

## Booleanos

### true | false

## null, undefined and NaN

`null` refere-se ao valor de nada (value of nothing)

`undefined` refere-se à ausência de valor (absence of value) - didn't assign a value

```js
var x = null;
var y; // undefined
```

`NaN` significa "Not-a-Number" e é constantemente retornado indicando um erro com operações numéricas.

```js
// calcular a raiz quadrada de um número negativo retornará NaN
Math.sqrt(-10);

// tentar dividir uma string por 5 retornará NaN
"hello" / 5;
```

## Igualdade

```js
"1" == 1;
0 == false;
```

> _Returns: true_

### Coerção de tipo implícita

JavaScript é uma linguagem fracamente tipada. Basicamente, isso significa que, quando você está escrevendo código JavaScript, não precisa especificar tipos de dados. Em vez disso, quando seu código é interpretado pelo mecanismo do JavaScript, ele automaticamente será convertido ao tipo de dado "apropriado". Isso é chamado de _coerção de tipo implícita_.

Uma linguagem fortemente tipada é uma linguagem de programação mais propícia a gerar erros se os dados não casarem com um certo tipo esperado. Devido ao fato de o JavaScript ser fracamente tipado, não há necessidade de você especificar tipos de dados; no entanto, isso pode levar a erros que são difíceis de diagnosticar, devido à coerção de tipo implícita.

Exemplo de código de uma linguagem de programação fortemente tipada:

```c
int count = 1;
string name = "Julia";
double num = 1.2932;
float price = 2.99;
```

Código equivalente em JavaScript

```js
var count = 1;
var name = "Julia";
var num = 1.2932;
var price = 2.99;
```

Quando você utiliza os operadores `==` ou `!=`, o JavaScript primeiro converte cada valor para o mesmo tipo (se eles já não são do mesmo tipo); por isso é chamado de "coerção de tipo"! Isso é frequentemente o comportamento que você não deseja e, na verdade, é considerada uma **má prática** utilizar os operadores `==` e `!=` ao se comparar valores para igualdade.

```js
"1" == true;
```

> _Returns: true_

### Igualdade estrita

Em vez disso, em JavaScript, é melhor utilizar igualdade estrita para ver se números, strings ou booleanos, etc. são idênticos em tipo e valor, sem realizar a conversão de tipos primeiramente. Para fazer uma comparação estrita, simplesmente adicione mais um símbolo de igual `=` ao final dos operadores `==` e `!=`.

```js
"1" === 1;
```

> _Returns: false_

---

Notas de estudos do curso [Intro to Javascript](https://www.udacity.com/course/intro-to-javascript--ud803) da [Udacity](https://www.udacity.com).
