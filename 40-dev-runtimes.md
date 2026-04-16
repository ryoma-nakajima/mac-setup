# 40. 開発ランタイム

## Node.js

`brew install node` でも OK だが、バージョン切替を使うなら:

```bash
brew install nvm
mkdir -p ~/.nvm
# .zshrc に
#   export NVM_DIR="$HOME/.nvm"
#   [ -s "$(brew --prefix)/opt/nvm/nvm.sh" ] && . "$(brew --prefix)/opt/nvm/nvm.sh"
nvm install --lts
npm i -g tsx pnpm
```

## Python

```bash
brew install uv
# プロジェクトごと: uv venv && uv pip install -r requirements.txt
```

## iOS / Swift

- Xcode は Mac App Store から（最新版）
- `sudo xcodebuild -license accept`
- `brew install cocoapods xcodegen mint`
- Xcode インストール後に `brew install swiftlint`
