## GNOME
```bash
sudo apt update
sudo apt upgrade -y
sudo apt install -y gnome-session-flashback
sudo reboot
sudo apt install $(check-language-support)
im-config -n fcitx
```
## swap 領域削除
```bash
sudo vi /etc/rc.local
```
exit 0 の前の行に追加
```
swapoff -a
```
## 閉じるボタンを右に表示
```bash
gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'
```

## デスクトップにゴミ箱表示
```bash
gsettings set org.gnome.nautilus.desktop trash-icon-visible true
```

## ホームディレクトリの表記を英語名に変更
```bash
LANG=C xdg-user-dirs-gtk-update
```
Don't ask me again にチェック

## 最近開いたドキュメント を無効
```bash
cd ~/.local/share/
rm recently-used.xbel
mkdir recently-used.xbel
```

## DATAドライブを自動マウント
```bash
sudo vi /etc/fstab
```
最後の行に追加
```
LABEL=DATA /mnt/DATA auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

## vim完全版をインストール
一旦削除してからインストール
```bash
sudo apt -y --purge remove vim-common vim-tiny
sudo apt install -y vim
```

## MP3再生可能にする
```bash
sudo apt install -y ubuntu-restricted-extras
```

## 実行権限のあるファイルをダブルクリックで実行できるようにする
```bash
gsettings set org.gnome.nautilus.preferences executable-text-activation ask
```

## Firefox 二重起動
* Firefox を終了しておく
```bash
firefox -P
```
* create
* デスクトップにショートカットを作成する
* ショートカットを右クリック -> プロパティ
* 「コマンド」に「firefox -P secondary」と記述
* アイコンを変更する

## デュアルブートにおける Windows の時間ずれ調整
### Windows 側
管理者権限でコマンドプロンプトを開く
```
reg add "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation" /v RealTimeIsUniversal /d 1 /t REG_DWORD /f
```
### やめる場合（元に戻す）
```
reg delete HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /f
```

# Ubuntu のアンインストール
## MBR 修復

```
bootrec /fixboot
bootrec /fixmbr
exit
```