# Como escrever boas mensagens de commit no git

## Quando fazer um *commit*? 

- Com frequência...
- Quando está em um estado do qual quer poder voltar
- Quando se finaliza uma unidade de trabalho, um aspecto do trabalho
- Não se limita ao número de linhas de código ou número de arquivos modificados
- Não dar *commits* quando o código não funciona

## Boas práticas nas mensagems de *commit*?

### Adotar padrões (style guide) no formato

Adotar uma convenção/padrão é uma boa prática para manter organizado o log das mensagens de commit. Um padrão legal é:

```bash
<type>[optional scope]: <description>

[optional body]

[optional footer]
```

O `type` e a `description` são obrigatórias, os demais campos são opcionais.

`type`pode ser:

- feat (new feature)
- fix (bug fix)
- docs (changes to documentation)
- style (formatting, missing semi colons, etc; no code change)
- refactor (refactoring production code)
- test (adding missing tests, refactoring tests; no production code change)
- chore (updating grunt tasks etc; no production code change)

[Udacity Git Commit Message Style Guide](https://udacity.github.io/git-styleguide/)
[Angular Commit Message Guidelines](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#-commit-message-guidelines)

### Escrever mensagem de commit sem conjunções aditivas

- Se na mensagem é necessário usar uma conjunção aditiva, como 'e' ("mudança x E mudança Y") então deveriam ser dois commits separados
- Isso não quer dizes que precise ser alteração em um só arquivo, mas que devem estar no mesmo contexto de mudança
- Ao commitar alterações menores é mais fácil escrever a mensagem de commit

### Referenciar e fechar issues/pull requests com a mensagem de commit

- Se um commit referencias uma issue ou pull request, adicionar isso à mensagem é legal
- No GitHub, ao se utilizar #NumeroIssue faz uma referência. Se usar as palavras "Fix #123, Fixes #123, Close #123" também já fecha automaticamente a issue/pull request.