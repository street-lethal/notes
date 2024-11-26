## GNOME
upgrade が20分程度
```bash
sudo apt update
sudo apt upgrade -y
```

## historyに時刻記録
```bash
echo "HISTTIMEFORMAT='%Y-%m-%dT%T%z '" >> ~/.bashrc
```
## Nautilus関連
### Nautilus デフォルトを一覧表示に
```bash
gsettings set org.gnome.nautilus.preferences default-folder-viewer 'list-view'
```

### 日時表示に秒を追加
```bash
gsettings set org.gnome.desktop.interface clock-show-seconds true
```

### 実行権限のあるファイルをダブルクリックで実行できるようにする
```bash
gsettings set org.gnome.nautilus.preferences executable-text-activation ask
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
LABEL=Data /mnt/Data auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

## vim完全版をインストール
一旦削除してからインストール
```bash
sudo apt -y --purge remove vim-common vim-tiny
sudo apt install -y vim
```
## 各種インストール

```
sudo dpkg -i google-chrome-stable_current_amd64.deb
sudo apt install -y usb-creator-gtk
``` 

## バックアップされた Firefox のプロファイルが稼働中の Firefox のバージョンと合わずに起動できない場合
```shell script
firefox -allow-downgrade
```

## Firefox で動画再生を可能にする
```shell script
sudo apt install -y ffmpeg
```

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
bootrec /fixmbr
exit
```

「 `bootrec /fixboot` 不要」説 (打たなくても動いた)

