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
