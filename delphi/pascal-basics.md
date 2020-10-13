# Pascal

- Fortemente tipada  
- Não diferencia maiúsculas e minúsculas (`minhaVar`, `minhavar` e `MINHAVAR` são equivalentes)  
- Espaços em branco são usados somente para legibilidade do código e não interferem na compilação  
- Você pode escrever uma 'declaração' (_statement_) em várias linhas de código  
- Final de uma declaração utiliza-se ponto e vírgula (`;`)

## Comentários

```pascal
{comentario}
(* comentario *)
// comentario de uma linha
```

## Variáveis

As variáveis podem ser _globais_ - quando declaradas dentro da Unit - ou _locais_ - quando declaradas dentro de `function` ou de  `procedure`.

As variáveis devem ser declaradas antes de serem usadas e sempre deve-se especificar o tipo.

```pascal
{declarar muitas variáveis de uma só vez}
var
  Value: Integer;
  IsCorrect: Boolean;
  A, B: Char;

{atribuir um valor inicial às variáveis, somente para variáveis globais}
var
  Value: Integer = 10;
  Correct: Boolean = True;
```

## Constantes

Para declarar uma constante não é necessário especificar o tipo de dado.

```pascal
{sem especificação do tipo}
const
  Thousand = 1000;
  Pi = 3.14;
  AuthorName = 'Marco Cantù';

{com especificação do tipo}
const
  Thousand: Integer = 1000;
```
