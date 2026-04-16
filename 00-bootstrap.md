# 00. Bootstrap（最優先）

新マシン開封後、**まずこの3つ**を入れる。あとは Claude Code と会話しながら進めれば残りは片付く。

```bash
# 1. Xcode Command Line Tools（Git・コンパイラ等の土台）
xcode-select --install

# 2. Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 2.1 PATH を永続化（Apple Silicon は /opt/homebrew、Intel は /usr/local）
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"

brew --version   # → Homebrew x.x.x が出れば OK

# 3. Claude Code（公式インストーラ / Node 不要）
curl -fsSL https://claude.ai/install.sh | bash

# 3.1 PATH を永続化
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
export PATH="$HOME/.local/bin:$PATH"

claude --version
claude login
```

ここまで来たら `claude` を起動して「`mac-setup/INDEX.md` の次のステップから順にセットアップして」と頼めばよい。

## 代替インストール手段（`curl | bash` が通らない場合）

**A. Homebrew cask**

```bash
brew install --cask claude-code
```

**B. npm**

```bash
brew install node          # or: brew install nvm && nvm install --lts
npm install -g @anthropic-ai/claude-code
```

## PATH トラブルシュート

`command not found: claude` になる場合、`.zshrc` に追記:

```bash
# npm global bin（node を brew で入れた場合は通常 /opt/homebrew/bin 配下で解決される）
export PATH="$(npm config get prefix)/bin:$PATH"

# nvm を使う場合は nvm の初期化より後ろに置くこと
```

追記後は `source ~/.zshrc` または新しいシェルで反映。

```bash
which claude            # → /opt/homebrew/bin/claude などが返れば OK
claude --version
claude login            # ブラウザが開いて認証
```
