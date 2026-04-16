# 50. シェル環境

```bash
# Oh My Zsh（好みで）
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## `.zshrc`

```bash
export PATH="$HOME/.local/bin:/opt/homebrew/bin:$PATH"
export EDITOR=code

# claude を c だけで起動
alias c="claude"

# VSCode 統合ターミナルのタブタイトル自動更新
# （シェル側から ESC シーケンスで title が変えられる状態にしておく）
```

## Git 初期設定

```bash
git config --global user.name "<Your Name>"
git config --global user.email "<your@email>"
git config --global init.defaultBranch main
git config --global pull.rebase false
gh auth login
```

> `user.name` / `user.email` の実値はコミット履歴に残るので、公開リポ用と業務用で使い分ける場合は `~/.gitconfig-work` などで includeIf 運用にする。

## ディレクトリ規約（最小限）

```bash
mkdir -p ~/_edit     # 事業ドキュメント集約
mkdir -p ~/_project  # 外部プロジェクト／OSS
```

命名規則は `~/_edit/CLAUDE.md` を参照。
