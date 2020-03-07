
# Básico

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

---

https://www.w3schools.com/python/default.asp