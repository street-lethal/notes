## gitignore_global
```bash
git config --global core.excludesfile ~/.gitignore_global
vi ~/.gitignore_global
```
### 設定例
```
.idea
*.iml
```

## MComix
```bash
sudo apt install -y mcomix
```

## Google Chrome プロファイルディレクトリ
```
~/.config/google-chrome/Default
```

## Ubuntu クリップボード
### インストール
```bash
sudo apt install -y xsel
```
### クリップボードへコピー
```bash
cat ~/clip.txt | xsel --clipboard --input
```
