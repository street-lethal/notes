# gitignore_global
```bash
git config --global core.excludesfile ~/.gitignore_global
vi ~/.gitignore_global
```
## 設定例
```
.idea
*.iml
```

# Google Chrome プロファイルディレクトリ
```
~/.config/google-chrome/Default
```

# 分割 & 結合
## 分割
* Unix
```bash
split filename.iso -b 500m -d filename.iso_
```
## 結合
* Unix
```bash
cat filename.iso_* > filename.iso
```
* Windows
```
copy /b filename.iso_* filename.iso
```

# evince(PDFリーダ) ショートカット
* `F9` サイドペイン表示/非表示

# update git
```bash
sudo add-apt-repository -y ppa:git-core/ppa
sudo apt update
sudo apt install git -y
```

# libdvdcss.so (Brasero で DVD リッピングに必要となるライブラリ) インストール
```sh
sudo apt -y install libdvd-pkg
sudo dpkg-reconfigure libdvd-pkg
``` 

# Ubuntu アプリケーションショートカット

(例) intellij

```
touch /usr/share/applications/intellij.desktop
vi /usr/share/applications/intellij.desktop
```

```
[Desktop Entry]
Version=13.0
Type=Application
Terminal=false
Icon[en_US]=/home/z/intellij/bin/idea.png
Name[en_US]=IntelliJ
Exec=/home/z/intellij/bin/idea.sh
Name=IntelliJ
Icon=/home/z/intellij/bin/idea.png
```
