## wine

(ファイルを指定せずにインストールする方法)
```sh
sudo apt install -y wine
sudo dpkg --add-architecture i386 && sudo apt update && sudo apt install -y wine32:i386
```

(ファイルを指定してダウンロードしてインストールする方法)
```sh
wget http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_9.0~repack-4build3_all.deb
sudo apt install -y ./wine_9.0~repack-4build3_all.deb
sudo dpkg --add-architecture i386 && sudo apt update && sudo apt install -y wine32:i386
```

## Kindle のブラウザー準備

```sh
wget https://dl.winehq.org/wine/wine-gecko/2.47.4/wine-gecko-2.47.4-x86.msi
wine msiexec /i wine-gecko-2.47.4-x86.msi
```
## Kindle

```sh
wine KindleForPC-installer-1.39.65383.exe
```

## Python + Library

```sh
wget https://www.python.org/ftp/python/3.8.10/python-3.8.10.exe
wine python-3.8.10.exe
wine pip install pycryptodome
```

## Generate Key

```sh
wget https://raw.githubusercontent.com/apprenticeharper/DeDRM_tools/refs/heads/master/DeDRM_plugin/kindlekey.py
wine python kindlekey.py 
```

kindlekey1.k4i が生成される

`環境設定` -> `プラグイン` -> `ファイル形式` -> `DeDRM` -> `プラグインをカスタマイズ` -> `Kindle for Mac/PC ebooks` -> `Import Existing Keyfiles` -> kindlekey1.k4i を選択
