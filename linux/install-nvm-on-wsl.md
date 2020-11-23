# Install NVM (node version manager) on WSL (Windows Subsystem for Linux)

- Installation

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```

- Add source line in ZSH

```bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

---

[nvm command not found](https://dev.to/duhbhavesh/nvm-command-not-found-1ho)
