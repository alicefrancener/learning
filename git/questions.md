# Questions

- [How to Update Fork Repo From Original Repo?](https://levelup.gitconnected.com/how-to-update-fork-repo-from-original-repo-b853387dd471)
  ```bash
  # Set the original repo as your upstream repo
  git remote add upstream <original repo>

  # Update your local Master to be in synch with the original repo
  git pull upstream master

  # Update the forked repo master by pushing the local repo up
  git push origin master
  ``` 

- [How to merge two or multiple git repositories into one](https://medium.com/altcampus/how-to-merge-two-or-multiple-git-repositories-into-one-9f8a5209913f)
  Considerando que há dois repositórios que você deseja unir (*merge*), `sub-projeto` e `projeto`:
  
  Entre no repositório no qual você quer combinar com o outro (ex.: dentro de `projeto` irei combinar o repo `sub-projeto`).

  ``` bash
  git remote add -f sub-projeto git@github.com:username/sub-projeto.git
  ```

  Combine os repositórios.
  ``` bash
  git merge sub-projeto/master --allow-unrelated-histories
  ```
  Nesse ponto, os repositórios foram combinados.
  * Uma dica para evitar conflitos entre arquivos é verificar antes os dois repositórios que serão combinados. Geralmente arquivos que estão na raiz como `.gitignore`, `LICENSE` and `README` geram conflitos, pois existem nos dois repositórios; eles podem ser renomeados ou movidos para outra pasta antes do `merge`.

## Tags

- Como listar tags?
  - `git tag`
- Como procurar por uma tag?
  - `git tag -l "v1.8.5*"`: procurar por tags "v1.8.5" (expressão regular)
- Como mostrar informações sobre uma tag?
  - `git show v1.4`: mostra informações sobre a tag v1.4
- Como criar tag?
  - `git tag -a v1.4 -m "my version 1.4"`: cria annotated tag (-a) com mensagem (-m)
- Como criar tag para um commit específico?
  - `git tag -a <nome-da-tag> <SHAcommit>`
- Como push uma tag?
  - Ao usar o `git push` ele não envia por padrão as tags
  - `git push origin <nome-da-tag>`: enviar a tag para origin
  - `git push origin --tags`: enviar todas as tags para remote que ainda não estão lá
- Como deletar tags local e remota?
  - `git tag -d <tagname>`: deletar tag localmente
  - `git push origin --delete <tagname>`: deletar tag remotamente
