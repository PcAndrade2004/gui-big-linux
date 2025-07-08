# gui-big-linux


Show, Paulo! Aqui vai um **guia completo e passo a passo** — desde instalar o `oh-my-posh`, baixar os temas, até configurar seu terminal com o `.bashrc` pronto (com o tema `paradox`, como pediu).

---

## ✅ GUIA COMPLETO – `oh-my-posh` no BigLinux (base Manjaro)

---

### 🛠️ 1. **Instalar o oh-my-posh**

```bash
sudo pacman -S oh-my-posh
```

---

### 🎨 2. **Baixar todos os temas oficiais**

```bash
mkdir -p ~/.poshthemes
cd ~/.poshthemes
wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/themes.zip
unzip themes.zip
chmod u+rw *.omp.json
rm themes.zip
```

> Agora você tem acesso a todos os temas `.omp.json`, como `paradox.omp.json`, `jandedobbeleer.omp.json`, etc.

---

### 🧾 3. **Substituir seu `.bashrc`**

Abra o `.bashrc` com seu editor favorito:

```bash
nano ~/.bashrc
```

Apague o conteúdo antigo e cole este abaixo:

---

```bash
# ~/.bashrc personalizado por ChatGPT para Paulo no BigLinux

# ---------------------------------------------------------
# Se o shell não for interativo, encerra aqui
[[ $- != *i* ]] && return

# ---------------- HISTÓRICO ----------------
HISTCONTROL=ignoredups:erasedups
HISTSIZE=10000
SAVEHIST=10000

# ---------------- ALIASES ------------------
alias ll='ls -lah --color=auto'
alias update='sudo pacman -Syu'
alias cls='clear'
alias grep='grep --color=auto'

# ---------------- COLOR PROMPT -------------
force_color_prompt=yes

# ---------------- PATH ---------------------
export PATH="$HOME/.local/bin:$HOME/bin:$PATH"

# ---------------- NVM ----------------------
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"

# ---------------- AUTOCOMPLETE -------------
if [ -f /usr/share/bash-completion/bash_completion ]; then
  . /usr/share/bash-completion/bash_completion
elif [ -f /etc/bash_completion ]; then
  . /etc/bash_completion
fi

# ---------------- FZF + RIPGREP ------------
if [ -f /usr/share/fzf/key-bindings.bash ]; then
  source /usr/share/fzf/key-bindings.bash
  fzf() {
    command fzf --preview 'bat --style=numbers --color=always {}' "$@"
  }
fi

# ---------------- OH-MY-POSH ----------------
# Tema: paradox (pode trocar por outro da pasta ~/.poshthemes)
eval "$(oh-my-posh init bash --config ~/.poshthemes/paradox.omp.json)"

# ---------------- EDITOR PADRÃO -------------
export EDITOR=nano

# ---------------- TERM FIX ------------------
export TERM=xterm-256color
```

---

### 💾 4. **Salvar e aplicar**

Salve com `Ctrl + O`, depois `Enter` e saia com `Ctrl + X`.

Agora aplique com:

```bash
source ~/.bashrc
```

---

### 👀 5. **Testar outros temas rapidamente (opcional)**

```bash
eval "$(oh-my-posh init bash --config ~/.poshthemes/jandedobbeleer.omp.json)"
```

---

### 🧪 Prévia de Temas Recomendados

| Tema                    | Estilo                      | Indicação                       |
| ----------------------- | --------------------------- | ------------------------------- |
| `paradox`               | Nerd/tech, moderno          | Ideal para devs                 |
| `jandedobbeleer`        | Clean + ícones e git status | Tema padrão mais usado          |
| `powerlevel10k_rainbow` | Estilo Zsh Powerlevel10k    | Muito colorido e completo       |
| `clean-detailed`        | Minimalista                 | Para quem gosta de simplicidade |
| `pure`                  | Super leve e objetivo       | Inspirado no tema do Zsh "Pure" |

---

![Captura de imagem_20250707_215800](https://github.com/user-attachments/assets/3f16d00b-ff0c-4ecc-bdac-e74d4b74fcaa)

