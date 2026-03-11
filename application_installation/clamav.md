# ClamAV

## インストール

```sh
sudo apt update
sudo apt install -y clamav clamav-daemon
```

## ウイルス定義ファイルの更新

```sh
sudo systemctl stop clamav-freshclam
sudo freshclam
sudo systemctl start clamav-freshclam
```

## スキャンの実行

### 特定のフォルダをスキャン
```sh
clamscan -r /path/to/dir
```

### 感染ファイルのみを表示
```sh
clamscan -r --infected /path/to/dir
```

### 感染ファイルを隔離する
```sh
clamscan -r --move=/path/to/quarantine /path/to/dir
```

### システム全体をスキャン
```sh
sudo clamscan -r / --exclude-dir=/sys
```
