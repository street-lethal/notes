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
#### 効かない場合
```bash
sudo cp /opt/Adobe/Reader9/Resource/Support/AdobeReader.desktop ~/.local/share/applications/
sudo vi ~/.local/share/applications/AdobeReader.desktop # 以下参照
```
* 修正前
```text
Exec=acroread
```
* 修正後
```text
Exec=acroread %f
```
PDFの右クリック -> `プロパティ` -> `開き方` -> `Adobe Reader` -> `デフォルトに設定する`

### Tips
* `Edit` -> `Preference`
  * `Full Screen` カテゴリ
    * `Full screen with one page at a time` のチェックをOFF
  * `Page Display` カテゴリ
    * `Page Layout`: `Two-Up`
    * `Zoom`: `Fit Page`
* `View` -> `Page Display`
  * `Show Cover Page During Two-Up`

## Rip DVD Audio
### transcode インストール
```bash
sudo apt install -y transcode
```
### チャプタ数確認
```bash
tcprobe -i /dev/sr0
```
以下のような行を探す。(この例ではチャプタ数は21)
```text
[dvd_reader.c] DVD title 1/1: 21 chapter(s), 1 angle(s), title set 1
```

### 変換
`21` の部分にはチャプタ数を入れる
```bash
for i in {1..21};do transcode -x null,dvd -y null,tcaud -i /dev/sr0 -T 1,$i,1 -a 0 -E 44100,16,2 --lame_preset medium -m ~/Music/`printf "%02d" $i`.mp3; done
```
