# 90. 最終チェック

## CLI / ランタイム

```bash
brew doctor
brew list --formula | wc -l   # だいたい 130 前後
node -v && python3 --version && deno --version
gh auth status
```

## GUI アプリ（cask + 直接インストール両対応）

`brew list --cask` だけでは直接インストールしたアプリが漏れる。`/Applications/` も合わせてチェック:

```bash
expected_apps=(
  "Google Chrome"
  "Brave Browser"
  "Visual Studio Code"
  "Raycast"
  "Alfred 5"
  "AppCleaner"
  "CleanShot X"
  "Notion"
  "Obsidian"
  "Claude"
  "OBS"
  "Docker"
  "Google Drive"
)

for app in "${expected_apps[@]}"; do
  if ls /Applications/ 2>/dev/null | grep -qi "$app"; then
    echo "✅ $app"
  elif brew list --cask 2>/dev/null | grep -qi "$(echo "$app" | tr ' ' '-')"; then
    echo "✅ $app (cask)"
  else
    echo "❌ $app — 未インストール"
  fi
done
```

## Mac App Store（mas）

```bash
mas_apps=(
  "497799835:Xcode"
  "937984704:Amphetamine"
  "539883307:LINE"
  "1429033973:RunCat"
)

installed=$(mas list 2>/dev/null)
for entry in "${mas_apps[@]}"; do
  id="${entry%%:*}"
  name="${entry##*:}"
  if echo "$installed" | grep -q "^$id"; then
    echo "✅ $name"
  else
    echo "❌ $name ($id) — 未インストール"
  fi
done
```

すべて ✅ なら OK。
