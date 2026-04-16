# 10. macOS 基礎

```bash
# Command Line Tools（Git等の土台）
xcode-select --install

# Rosetta（Apple Silicon で Intel バイナリを動かす保険）
softwareupdate --install-rosetta --agree-to-license
```

## システム設定（先にやっておくと楽）

- Apple ID サインイン
- iCloud Drive / Google Drive にログイン
- トラックパッド・キーボード設定
- Finder「パスバー表示」「ステータスバー表示」「拡張子を常に表示」

### バッテリー残量をメニューバーに表示

```bash
defaults write com.apple.controlcenter "NSStatusItem Visible Battery" -bool true
defaults write ~/Library/Preferences/ByHost/com.apple.controlcenter Battery -dict-add ShowPercentage -bool true
```

> 反映されない場合: システム設定 → コントロールセンター → バッテリー →「割合（%）を表示」ON

### ディスプレイ解像度（スケーリング 1680 x 1050）

システム設定 → ディスプレイ → 「スペースを拡大」側にスライドして 1680 x 1050 を選択。

> CLI で設定する場合は `displayplacer` が使える:
>
> ```bash
> brew tap jakehilborn/jakehilborn
> brew install displayplacer
> displayplacer list                    # 現在の設定確認
> displayplacer "id:<ID> res:1680x1050 scaling:on"
> ```

### Dock

```bash
# サイズを小さめに（15% ≒ tilesize 33）
defaults write com.apple.dock tilesize -int 33

# アプリの提案と最近使用したアプリを非表示
defaults write com.apple.dock show-recents -bool false

# 反映
killall Dock
```

## Caps Lock → Cmd リマップ（最優先）

Caps Lock を左 Cmd として使う設定。`hidutil` で一度設定し、LaunchAgent でログイン時に自動適用。

```bash
# 即時適用（動作確認）
hidutil property --set '{"UserKeyMapping":[{"HIDKeyboardModifierMappingSrc":0x700000039,"HIDKeyboardModifierMappingDst":0x7000000E3}]}'

# 永続化: LaunchAgent を作成
cat > ~/Library/LaunchAgents/com.local.KeyRemapping.plist <<'EOF'
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.local.KeyRemapping</string>
    <key>ProgramArguments</key>
    <array>
        <string>/usr/bin/hidutil</string>
        <string>property</string>
        <string>--set</string>
        <string>{"UserKeyMapping":[{"HIDKeyboardModifierMappingSrc":0x700000039,"HIDKeyboardModifierMappingDst":0x7000000E3}]}</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
</dict>
</plist>
EOF

launchctl load ~/Library/LaunchAgents/com.local.KeyRemapping.plist
launchctl list | grep KeyRemapping   # 登録確認
```

- `0x700000039` = Caps Lock
- `0x7000000E3` = Left Command

解除する場合:

```bash
launchctl unload ~/Library/LaunchAgents/com.local.KeyRemapping.plist
rm ~/Library/LaunchAgents/com.local.KeyRemapping.plist
```
