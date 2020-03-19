# Tags
- [Tags](#tags)
  - [Listar e ver tags](#listar-e-ver-tags)
  - [Criar tags (annotated -a)](#criar-tags-annotated--a)
  - [Criar tag para um commit específico](#criar-tag-para-um-commit-espec%c3%adfico)
  - [Pushing tag](#pushing-tag)
  - [Deletar tag](#deletar-tag)

## Listar e ver tags 

`git tag`: lista tags
`git tag -l "v1.8.5*"`: procurar por tags "v1.8.5" (expressão regular)
`git show v1.4`: mostra informações sobre a tag v1.4

## Criar tags (annotated -a)

`git tag -a v1.4 -m "my version 1.4"`: cria annotated tag (-a) com mensagem (-m)

## Criar tag para um commit específico

`git tag -a <nome-da-tag> <SHAcommit>`

## Pushing tag

Ao usar o `git push` ele não envia por padrão as tags

`git push origin <nome-da-tag>`: enviar a tag para origin
`git push origin --tags`: enviar todas as tags para remote que ainda não estão lá

## Deletar tag

`git tag -d <tagname>`: deletar tag localmente
`git push origin --delete <tagname>`: deletar tag remotamente

---

https://git-scm.com/book/en/v2/Git-Basics-Tagging