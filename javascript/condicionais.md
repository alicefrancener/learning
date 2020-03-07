# Condicionais

- [Condicionais](#condicionais)
  - [Declarações if...else](#declara%c3%a7%c3%b5es-ifelse)
  - [Declaração else if](#declara%c3%a7%c3%a3o-else-if)
  - [Operadores lógicos](#operadores-l%c3%b3gicos)
  - [Tabelas verdade](#tabelas-verdade)
    - [&& (AND)](#and)
    - [|| (OR)](#or)
  - [Valores falsos](#valores-falsos)
  - [Valores verdadeiros](#valores-verdadeiros)
  - [Operador ternário](#operador-tern%c3%a1rio)
  - [Switch](#switch)
  - [Break](#break)

## Declarações if...else

Declarações if...else permitem que você execute certos pedaços de código com base em um condição ou conjunto de instruções a ser cumprido.

```js
if (/* se esta expressão for verdadeira */) {
  // execute este código
} else {
  // execute este código
}
```

## Declaração else if

Em JavaScript, você pode representar esta verificação secundária usando uma declaração if extra, chamada de declaração else if.

```js
var weather = "sunny";

if (weather === "snow") {
  console.log("Traga um casaco.");
} else if (weather === "rain") {
  console.log("Traga uma jaqueta de chuva.");
} else {
  console.log("Vista o que você já está vestindo.");
}
```

## Operadores lógicos

Operadores lógicos podem ser usados em conjunto com valores booleanos (`verdadeiro` e `falso`) para criar expressões lógicas complexas.

Combinando dois valores booleanos juntos a um operador lógico, você cria uma expressão lógica que retorna um outro valor booleano. Aqui está uma tabela descrevendo os diferentes operadores lógicos:

| Operador | Significado | Exemplo              | Como funciona                                                                                    |
| -------- | ----------- | -------------------- | ------------------------------------------------------------------------------------------------ |
| `&&`     | lógico E    | `valor1 && valor2`   | Retorna `verdadeiro` se ambos o `valor1` e o `valor2` forem avaliados como `verdadeiro`          |
| `\|\|`   | lógico OU   | `valor1 \|\| valor2` | Retorna `verdadeiro` se `valor1` ou `valor2` (ou mesmo ambos!) forem avaliados como `verdadeiro` |
| `!`      | lógico NÂO  | `!valor1`            | Retorna o oposto do `valor1`. Se `valor1` é `verdadeiro`, então `!valor1` é `falso`              |

## Tabelas verdade

Tabelas verdade são uma forma de representar todas as combinações possíveis de inputs para uma expressão lógica.

### && (AND)

| A          | B          | A && B     |
| ---------- | ---------- | ---------- |
| verdadeiro | verdadeiro | verdadeiro |
| verdadeiro | falso      | falso      |
| falso      | verdadeiro | falso      |
| falso      | falso      | falso      |

### || (OR)

| A          | B          | A \|\| B   |
| ---------- | ---------- | ---------- |
| verdadeiro | verdadeiro | verdadeiro |
| verdadeiro | falso      | verdadeiro |
| falso      | verdadeiro | verdadeiro |
| falso      | falso      | falso      |

Em ambas as tabelas, existem cenários específicos onde, independentemente do valor de `B`, o valor de `A` é suficiente para satisfazer a condição.

Por exemplo, se você olhar `A` E `B`, se `A` é falso, então, independentemente do valor de `B`, a expressão total sempre será avaliada como falso, porque ambos `A` _e_ `B` devem ser verdadeiros, de forma que a expressão inteira seja avaliada como verdadeira.

Esse comportamento é chamado de **curto-circuito** porque ele descreve o evento quando argumentos mais à direita da expressão lógica não são considerados, pois o primeiro argumento já satisfaz a condição.

## Valores falsos

Um valor é _falso_ se ele converte para `false` quando avaliado em um contexto booleano. Por exemplo, uma string vazia `""` é falsa porque `""` é avaliada como `false`.

Valores falsos em JavaScript:

1. o valor booleano `false`
2. o tipo `null`
3. o tipo `undefined`
4. o número `0`
5. a string vazia `""`
6. o valor `NaN`

## Valores verdadeiros

Um valor é _verdadeiro_ se ele converte para `true` quando avaliado em um contexto booleano. Por exemplo, o número `1` é verdadeiro porque `1` é avaliado como `true`.

Exemplos de valores verdadeiros

```js
42;
("pizza");
("0");
("null");
("undefined");
{
}
[];
```

Essencialmente, se não estiver na lista dos valores falsos, então ele é verdadeiro!

## Operador ternário

O operador ternário provê a você uma alternativa para escrever declarações if...else robustas.

```js
condicional ? (se condicional é verdadeiro) : (se condicional é falso)
```

Para usar o operador ternário, primeiro forneça uma declaração condicional do lado esquerdo de `?`. Então, entre o `?` e `:`, escreva o código que seria executado se a condição fosse verdadeira e, ao lado direito de `:`, escreva o código que seria executado se a condição fosse falsa.

```js
var isGoing = true;
var color = isGoing ? "green" : "red";
```

## Switch

Uma declaração switch é uma outra forma de encadear múltiplas declarações else if que são **baseadas no mesmo valor sem usar declarações condicionais**. Em vez disso, você apenas troca o pedaço de código que é executado com base em um valor.

```js
var option = 3;

switch (option) {
  case 1:
    console.log("Você selecionou a opção  1.");
  case 2:
    console.log("Você selecionou a opção  2.");
  case 3:
    console.log("Você selecionou a opção  3.");
  case 4:
    console.log("Você selecionou a opção  4.");
  case 5:
    console.log("Você selecionou a opção  5.");
  case 6:
    console.log("Você selecionou a opção  6.");
}
```

> _Returns:_  
> Você selecionou a opção 3.  
> Você selecionou a opção 4.  
> Você selecionou a opção 5.  
> Você selecionou a opção 6.

Quando a declaração switch primeiro avalia, ela procura pela primeira cláusula `case` onde a expressão é avaliada para o mesmo valor obtido como resultado da expressão passada na declaração switch. Então, ela transfere o controle para tal cláusula `case`, executando os comandos associados. Mas ele não previne os casos abaixo de serem executados. Esse comportamento se chama **falling through**.

## Break

A declaração break pode ser usada para terminar uma declaração switch e transferir o controle do código para o código que segue a declaração terminada. Adicionando um `break` em cada cláusula case, você conserta o problema da declaração switch cair entre outras cláusulas case.

```js
var option = 3;

switch (option) {
  case 1:
    console.log("Você selecionou a opção 1.");
    break;
  case 2:
    console.log("Você selecionou a opção 2.");
    break;
  case 3:
    console.log("Você selecionou a opção 3.");
    break;
  case 4:
    console.log("Você selecionou a opção 4.");
    break;
  case 5:
    console.log("Você selecionou a opção 5.");
    break;
  case 6:
    console.log("Você selecionou a opção 6.");
    break; // tecnicamente, não necessário
}
```

> _Returns:_ Você selecionou a opção 3.

---

Notas de estudos do curso [Intro to Javascript](https://www.udacity.com/course/intro-to-javascript--ud803) da [Udacity](https://www.udacity.com).
