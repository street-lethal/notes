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
改行コードを除去してコピーする場合
```bash
echo -n `cat ~/clip.txt` | xsel --clipboard --input
```

## MP3Gain
* [pkgs.org](https://ubuntu.pkgs.org/14.04/ubuntu-universe-amd64/mp3gain_1.5.2-r2-6_amd64.deb.html)  より [mp3gain_1.5.2-r2-6_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/m/mp3gain/mp3gain_1.5.2-r2-6_amd64.deb) をダウンロード  
※Ubuntu16.04 のリポジトリにはないので 14.04 のリポジトリを使用
* ダウンロードした mp3gain_1.5.2-r2-6_amd64.deb を実行してインストール
* `Ubuntuソフトウェア` より `mp3gain` で検索し、 `easyMP3Gain` (GTK版とQT版とあるがQT版) をインストール

## Adobe Reader
### インストール
```bash
sudo add-apt-repository "deb http://archive.canonical.com/ precise partner"
sudo apt update
sudo apt install -y adobereader-enu
sudo add-apt-repository -r "deb http://archive.canonical.com/ precise partner"
sudo apt update
```
### デフォルトアプリケーション変更
```bash
cd /etc/gnome
sudo git init .
sudo git add .
sudo git commit -m "first commit"
sudo vi defaults.list # 以下参照
nautilus -q
```
#### /etc/gnome/defaults.list
* 修正前
```text
application/pdf=evince.desktop
```
* 修正後
```text
application/pdf=acroread.desktop
```
### Tips
* `Edit` -> `Preference`
  * `Full Screen` カテゴリ
    * `Full screen with one page at a time` のチェックをOFF
  * `Page Display` カテゴリ
    * `Page Layout`: `Two-Up`
    * `Zoom`: `Fit Page`
* `View` -> `Page Display`
  * `Show Cover Page During Two-Up`
