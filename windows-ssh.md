## 鍵認証方式設定

* 公開鍵を `C:\ProgramData\ssh\administrators_authorized_keys` におく
* 公開鍵の権限を設定する
  ```
  icacls.exe "C:\ProgramData\ssh\administrators_authorized_keys" /inheritance:r /grant "Administrators:F" /grant "SYSTEM:F"
  ```
* sshd 設定ファイル (`C:\ProgramData\ssh\sshd_config`) 編集
  ```
  PubkeyAuthentication yes
  ```
  ```
  PasswordAuthentication no
  ```

## SSH サーバ起動準備

### 以下2ファイルを C: 直下に配置

* [windows_ssh/start-ssh.ps1](windows_ssh/start-ssh.ps1)
* [windows_ssh/stop-ssh.ps1](windows_ssh/stop-ssh.ps1)

### 以下2ファイルをデスクトップに配置

* [windows_ssh/start_ssh.bat](windows_ssh/start_ssh.bat)
* [windows_ssh/stop_ssh.bat](windows_ssh/stop_ssh.bat)

## SSH サーバ起動

デスクトップの `start_ssh.bat` を管理者権限で実行

## SSH サーバ停止

デスクトップの `stop_ssh.bat` を管理者権限で実行
