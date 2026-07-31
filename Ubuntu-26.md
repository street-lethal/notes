## GNOME
upgrade が20分程度
```sh
sudo apt update
sudo apt upgrade -y
```

## historyに時刻記録
```sh
echo "HISTTIMEFORMAT='%Y-%m-%dT%T%z '" >> ~/.bashrc
```
## Nautilus関連
### Nautilus デフォルトを一覧表示に
```sh
gsettings set org.gnome.nautilus.preferences default-folder-viewer 'list-view'
```

### 日時表示に秒を追加
```sh
gsettings set org.gnome.desktop.interface clock-show-seconds true
```

### 日付と時刻のフォーマットをシンプル(例: "1か月前")から詳細(例: "2006/1/2 15:04")に変更
```sh
gsettings set org.gnome.nautilus.preferences date-time-format 'detailed'
```

### ターミナルを透過
```sh
dconf write /org/gnome/Ptyxis/Profiles/$(dconf read /org/gnome/Ptyxis/default-profile-uuid | tr -d "'")/opacity 0.85
```

## ホームディレクトリの表記を英語名に変更
```sh
LANG=C xdg-user-dirs-gtk-update
```
Don't ask me again にチェック

## 最近開いたドキュメント を無効
```sh
cd ~/.local/share/
rm recently-used.xbel
mkdir recently-used.xbel
```

## DATAドライブを自動マウント
```sh
sudo vi /etc/fstab
```
最後の行に追加
```
LABEL=Data /mnt/Data auto nosuid,nodev,nofail,x-gvfs-show,gid=1000,uid=1000,dmask=022,fmask=133 0 0
```

## vim完全版をインストール
一旦削除してからインストール
```sh
sudo apt -y --purge remove vim-common vim-tiny
sudo apt install -y vim
```

## Firefox を更新
```sh
sudo snap refresh firefox
```

## 各種インストール

```
sudo dpkg -i google-chrome-stable_current_amd64.deb
sudo apt install -y usb-creator-gtk file-roller
``` 

(file-roller で、パスワード付 zip ファイルを解凍せずに中身のファイルだけ開くには 7z が必要)

## キーボード設定 (英字配列の場合)

* `Ubuntu 設定` > `日本語(Mozc)` > `設定` > `一般`タブ > `キー設定の選択` > `編集`
* 以下2のエントリーを追加

|モード      |入力キー  |コマンド    |
|------------|----------|------------|
|直接入力    |Ctrl Space|IME を有効化|
|入力文字なし|Ctrl Space|IME を無効化|

## バックアップされた Firefox のプロファイルが稼働中の Firefox のバージョンと合わずに起動できない場合
```shell script
firefox -allow-downgrade
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

