# Branch

| Comando                                   | Ação                                     |
| ----------------------------------------- | ---------------------------------------- |
| `git branch`                              | listar branch                            |
| `git branch -v`                           | listar último commit de cada branch      |
| `git branch <branch>`                     | criar novo branch                        |
| `git checkout -b <branch>`                | criar novo branch e mudar pra branch     |
| `git branch -d <branch>`                  | deletar branch (seguro)                  |
| `git branch -D <branch>`                  | deletar (à força) branch                 |
| `git branch -m <branch>`                  | renomear branch atual                    |
| `git merge <branch-to-merge>`             | merge branch atual com `branch-to-merge` |
| `git push --set-upstream origin <branch>` | push branch para repositório remoto      |
| `git push origin --delete <branch>`       | excluir branch remoto                    |
| `git push origin :<branch>`               | excluir branch remoto                    |
| `git branch --merged`                     | listar merged branches                   |
| `git branch --no-merged`                  | listar não merged branches               |

---

- https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell
- https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging
- https://www.atlassian.com/br/git/tutorials/using-branches
