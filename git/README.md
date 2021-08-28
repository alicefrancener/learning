# Git

- [Questions](questions.md)
- [Resources](resources.md)
## Other
- [Installing gh on Linux](https://github.com/cli/cli/blob/trunk/docs/install_linux.md) 
- [Branch](./branch.md)
- [Guidelines para commit messages](./commit-messages-guidelines.md)
- [Professional Guides: Workflow Strategies](https://www.youtube.com/watch?v=aJnFGMclhU8)

## How to
- **Disable all paging in git**: [link](https://git-scm.com/docs/git-config#Documentation/git-config.txt-corepager)
  - `git config --global core.pager cat`

- **Track a remote branch locally**: [link](https://git-scm.com/docs/git-checkout)
  - A. `git checkout --track <remote>/<branch>`
  - B. `git checkout -b fix-failing-tests origin/fix-failing-tests`
    - it creates a new branch called fix-failing-tests
    - it checkouts that branch
    - it pulls changes from origin/fix-failing-tests to that branch

- **Move a commit to another branch in git**: [link](https://dev.to/projectpage/how-to-move-a-commit-to-another-branch-in-git-4lj4) 
  - In the target branch
    - `git cherry-pick <commit SHA>`
  - Change to the other branch and delete the commit
    - `git reset --hard <commit SHA>` 

- `git branch -a`: See both local and remote branches
- `git branch -r`: See only remote branches

## File's states
[Git Basics - Recording Changes to the Repository](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)
 - Each file in your working directory can be in one of two states: **tracked** or **untracked**
 - Tracked can be: _unmodified_, _modified_, or _staged_ 
 
 ![image](https://user-images.githubusercontent.com/42686542/127414395-ea7d6aab-9a28-40bc-a396-f2173d68096a.png)
