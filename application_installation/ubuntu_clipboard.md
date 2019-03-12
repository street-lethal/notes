# Ubuntu クリップボード
## インストール
```bash
sudo apt install -y xsel
```
## クリップボードへコピー
```bash
cat ~/clip.txt | xsel --clipboard --input
```
改行コードを除去してコピーする場合
```bash
echo -n `cat ~/clip.txt` | xsel --clipboard --input
```
