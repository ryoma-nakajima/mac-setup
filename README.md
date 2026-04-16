# mac-setup

新規 Mac（macOS / Apple Silicon 想定）を、このマシンと同じ開発・秘書環境に揃えるためのセットアップ手順。

## 進め方

**まず [`00-bootstrap.md`](00-bootstrap.md) だけ実行すれば `brew` + `claude` が揃う**。あとは Claude Code と対話しながら順に進めればよい。

旧マシンから移行する場合は [`brewfile.md`](brewfile.md) が最速。

## 目次

| # | ファイル | 内容 |
| --- | --- | --- |
| 00 | [bootstrap](00-bootstrap.md) | Xcode CLT + Homebrew + Claude Code（最優先2+1） |
| 10 | [macos-basics](10-macos-basics.md) | OS設定 / Caps Lock → Cmd リマップ |
| 20 | [brew-formula](20-brew-formula.md) | CLI ツール（`brew install`） |
| 30 | [brew-cask](30-brew-cask.md) | GUI アプリ（`brew install --cask` + `mas`） |
| 40 | [dev-runtimes](40-dev-runtimes.md) | Node / Python / iOS Swift |
| 50 | [shell](50-shell.md) | zsh / `.zshrc` / git 初期設定 |
| 60 | [devices](60-devices.md) | USB-UART ドライバ / マイコン |
| 90 | [final-check](90-final-check.md) | 動作確認 |
| - | [brewfile](brewfile.md) | Brewfile で一括復元 |

Claude Code の設定（`settings.json` / スキル / MCP）は別途管理。
