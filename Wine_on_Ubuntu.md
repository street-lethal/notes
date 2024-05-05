## wine

```sh
sudo apt install -y wine
sudo dpkg --add-architecture i386 && sudo apt-get update && sudo apt-get install wine32:i386
```

## Kindle

```sh
wine KindleForPC-installer-1.39.65383.exe
wget https://dl.winehq.org/wine/wine-gecko/2.47.4/wine-gecko-2.47.4-x86.msi
wine msiexec /i wine-gecko-2.47.4-x86.msi
```

## Python + Library

```sh
wget https://www.python.org/ftp/python/3.8.10/python-3.8.10.exe
wine python-3.8.10.exe
wine pip install pycryptodome
```

## Generate Key

https://github.com/apprenticeharper/DeDRM_tools/blob/master/DeDRM_plugin/kindlekey.py からソースコードファイルをダウンロード

```sh
wine python kindlekey.py 
```

kindlekey1.k4i が生成される

`環境設定` -> `プラグイン` -> `ファイル形式` -> `DeDRM` -> `プラグインをカスタマイズ` -> `Kindle for Mac/PC ebooks` -> `Import Existing Keyfiles` -> kindlekey1.k4i を選択
