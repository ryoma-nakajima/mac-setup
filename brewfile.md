# Brewfile 運用（最速レシピ）

旧マシンで定期的にダンプ:

```bash
brew bundle dump --file=~/Dropbox/dotfiles/Brewfile --force --describe
```

新マシンで復元:

```bash
brew bundle --file=~/Dropbox/dotfiles/Brewfile
```

これが一番早い。個別の手順書（`20-brew-formula.md` / `30-brew-cask.md`）は「Brewfile が壊れたとき」の保険として使う。
