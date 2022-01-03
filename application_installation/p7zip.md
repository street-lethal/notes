# p7zip-full

## インストール
```shell
sudo apt install -y p7zip-full
```

## 圧縮
```shell
7z a -tzip -p -mem=AES256 OUTPUT_FILE.7z UNZIPPED_DIRECTORY
```

## 解凍
```shell
7z x ZIPPED_FILE.7z
```

## 暗号化方式確認
```shell
7z l -slt ZIPPED_FILE
```
