
# Básico
- [Básico](#b%c3%a1sico)
  - [Execução](#execu%c3%a7%c3%a3o)
  - [Indentação](#indenta%c3%a7%c3%a3o)
  - [Comentários](#coment%c3%a1rios)
  - [Obtendo ajuda](#obtendo-ajuda)
  - [print()](#print)

Python:
  - linguagem interpretada
  - tipagem dinâmica
  - case sensitive
  - designed for readability
  - usa novas linhas para indicar um comando diferente de outras linguagens que utilizam `;`
  - escopo é definido por indentação (ao invés de `{}`)
  - utiliza por convenção o padrão Snake_Case para nomes de variáveis (ou identificadores).

## Execução

- Programas em Python podem ser executados diretamente na linha de comando após usar o comando `python` ou criando um arquivo `.py` e executando na linha de comando `python myfile.py`

## Indentação

- Python usa indentação para indicar um bloco de código e não somente para legibilidade.
- O número de espaços pode ser definido pelo programador, mas deve haver pelo menos um espaço
- Para cada bloco de código o número de espaços deve ser consistente

## Comentários

- Comentários de linha começam com `#`
- Também pode ser utilizada uma multiline string com propósito de comentário. Mas no fim das contas ela é uma string que não foi atribuída a uma variável

```python
#This is a comment.
print("Hello, World!")

print("Hello, World!") #This is another comment

"""
This is a comment
written in
more than just one line
"""
```

## Obtendo ajuda

Para obter ajudar usar a função `help()`:
```python
help(print)

"""
Retorna um relatório sobre a função print

print(value, ..., sep=' ', end='\n', file=sys.stdout,flush=False)
"""
``` 

## print()

A função `print` pode receber três argumentos:
- `value` é o valor que queremos imprimir, as reticências indicam que a função pode receber mais de um valor, basta separá-los por vírgula.
- `sep` é o separador entre os valores, por padrão o separador é um espaço em branco.
- `end` é o que acontecerá ao final da função, por padrão há uma quebra de linha, uma nova linha (`\n`).
  
```python
subst = "Python"
verbo = "é"
adjetivo = "fantástico"
print(subst, verbo, adjetivo, sep="_", end="!\n")

# retorna
# Python_é_fantástico!
```

---

- [Curso Alura: Python 3](https://www.alura.com.br/curso-online-python-3-introducao-a-nova-versao-da-linguagem?gclid=Cj0KCQiAqY3zBRDQARIsAJeCVxP-Ag55qq4Dkdn96JyrWNBFyShMf3_KAOM-iY0o14u4bw8axUzTNr0aAi0kEALw_wcB)
- https://www.w3schools.com/python/default.asp