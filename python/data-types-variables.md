# Variáveis e tipos de dados

- [Variáveis e tipos de dados](#vari%c3%a1veis-e-tipos-de-dados)
  - [Variáveis](#vari%c3%a1veis)
  - [Nomes de variáveis](#nomes-de-vari%c3%a1veis)

## Variáveis

- Tipagem dinâmica
- Não é obrigatório definir explicitamente o tipo da variável
- O tipo da variável depende do valor que passarmos para ela
- A variável só é criada quando atribuímos valor à ela
- Função `type` retorna qual o tipo da variável

```python
>>> pais = "Italia"
>>> quantidade = 4
>>> type(pais)
<class 'str'>
>>> type(quantidade)
<class 'int'>
```

- Tipo da variável pode mudar de acordo com o valor atribuído (**tipagem dinâmica**)

```python
>>> pais = "Brasil"
>>> type(pais)
<class 'str'>
>>> pais = 644
>>> type(pais)
<class 'int'>
```

## Nomes de variáveis

- A variable name must start with a letter or the underscore character
- A variable name cannot start with a number
- A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and _ )
- Variable names are case-sensitive (age, Age and AGE are three different variables)

***

- [Curso Alura: Python 3](https://www.alura.com.br/curso-online-python-3-introducao-a-nova-versao-da-linguagem?gclid=Cj0KCQiAqY3zBRDQARIsAJeCVxP-Ag55qq4Dkdn96JyrWNBFyShMf3_KAOM-iY0o14u4bw8axUzTNr0aAi0kEALw_wcB)
- https://www.w3schools.com/python/python_variables.asp
- https://www.w3schools.com/python/python_datatypes.asp