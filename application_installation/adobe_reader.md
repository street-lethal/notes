# Adobe Reader
## インストール
```bash
sudo add-apt-repository "deb http://archive.canonical.com/ precise partner"
sudo apt update
sudo apt install -y adobereader-enu
sudo add-apt-repository -r "deb http://archive.canonical.com/ precise partner"
sudo apt update
```
## デフォルトアプリケーション変更
```bash
cd /etc/gnome
sudo git init .
sudo git add .
sudo git commit -m "first commit"
sudo vi defaults.list # 以下参照
nautilus -q
```
### /etc/gnome/defaults.list
* 修正前
```text
application/pdf=evince.desktop
```
* 修正後
```text
application/pdf=acroread.desktop
```
### 効かない場合
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

## Tips
* `Edit` -> `Preference`
  * `Full Screen` カテゴリ
    * `Full screen with one page at a time` のチェックをOFF
  * `Page Display` カテゴリ
    * `Page Layout`: `Two-Up`
    * `Zoom`: `Fit Page`
* `View` -> `Page Display`
  * `Show Cover Page During Two-Up`
