# 90. 最終チェック

```bash
brew doctor
brew list --formula | wc -l   # だいたい 130 前後
brew list --cask
node -v && python3 --version && deno --version
gh auth status
```

すべて通れば OK。ここまで来たら Claude Code の構築（[`../claude-code.md`](../claude-code.md)）に進む。
