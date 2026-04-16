# 20. Homebrew formula（CLI）

```bash
brew install \
  git gh mosh tmux \
  node deno ollama \
  python@3.13 python@3.14 uv ruby \
  jq yq ripgrep fd pandoc p7zip \
  ffmpeg exiftool yt-dlp \
  imagemagick poppler \
  gnupg pinentry-mac \
  mysql sqlite supabase stripe \
  cocoapods xcodegen mint \
  arduino-cli platformio minicom \
  cppcheck llvm \
  cliclick terminal-notifier \
  gemini-cli
```

依存ライブラリ（`openssl`, `libpng`, `harfbuzz`, `cairo`, `sdl2` …）は上記のどれかが自動で引っ張るので個別指定不要。

## ⚠️ swiftlint は含めない

完全版 Xcode.app が必須のため、Command Line Tools のみの状態で入れようとすると**バッチ全体が abort し、他の formula も一切 install されない**（fetch ✔︎ は出るが Cellar は空のまま）。

→ **先に Xcode を Mac App Store から入れて `sudo xcodebuild -license accept` した後**、単独で `brew install swiftlint`。
