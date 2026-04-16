# 30. Homebrew cask（GUI）+ mas

```bash
# sudo 不要なアプリ（まずこっちを一気に入れる）
brew install --cask \
  google-chrome brave-browser \
  visual-studio-code \
  raycast alfred \
  appcleaner cleanshot \
  notion obsidian \
  claude \
  obs \
  silicon-labs-vcp-driver

# 外部 tap
brew install --cask hamed-elfayome/claude-usage/claude-usage-tracker

# sudo パスワード入力が必要なアプリ（1つずつ or 対話的に）
brew install --cask docker
brew install --cask google-drive
brew install --cask wch-ch34x-usb-serial-driver
```

## ⚠️ cask は fail-fast

1つでも「cask が存在しない」「ダウンロード失敗」「sudo パスワード必要」で止まると、**それ以降のアプリは一切 install されない**。

→ 安全策:

```bash
for c in cask1 cask2 cask3; do brew install --cask "$c"; done
```

で1つずつ流すと、失敗しても他は進む。

## ⚠️ cask に存在しないアプリ

過去リストに入れていたが実際は使えない:

- `amphetamine` → Mac App Store のみ（`mas install 937984704`）
- `line` → Mac App Store のみ（`mas install 539883307`）

## Mac App Store（mas）

```bash
brew install mas
mas install 497799835   # Xcode（swiftlint 前提条件）
mas install 937984704   # Amphetamine
mas install 539883307   # LINE
mas install 1429033973  # RunCat
# 他は `mas search <名前>` で ID 調査
```

## 手動ダウンロードが必要なもの

Homebrew cask に無いアプリ（公式サイトから DL）:

- **Microsoft 365**（Word / Excel / PowerPoint）— 法人アカウントでログイン
- **Aqua Voice**（音声入力）
- **FocuSee / Rotato**（画面収録・3Dモック）
- **Transporter**（App Store Connect 用）
- **Rive Early Access**

## GUI アプリ初期設定（個人設定）

### Raycast

- `Cmd + Shift + C` → Clipboard History を開くように設定
  - Raycast 設定 → Extensions → Clipboard History → Hotkey に `⌘⇧C` を割り当て

### CleanShot X

- `Cmd + 5` → All-in-One を開くように設定
  - CleanShot X 設定 → Shortcuts → All-in-One に `⌘5` を割り当て
