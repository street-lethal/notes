# Samba Ubuntu

```bash
sudo apt-get install -y samba
sudo pdbedit -a $USER
sudo cp -a /etc/samba/smb.conf /etc/samba/smb.conf.org
sudo vi /etc/samba/smb.conf # 編集方法は以下
sudo systemctl restart smbd
sudo systemctl restart nmbd
```
ufw設定してある場合は以下も実行
```bash
sudo ufw allow 137
sudo ufw allow 138
sudo ufw allow 139
sudo ufw allow 445

# 全てのポートを開放する場合は以下
# sudo ufw default ALLOW
```

### /etc/samba/smb.conf
* 差分が以下のようになるよう修正する
```bash
$ diff -uprN /etc/samba/smb.conf.org /etc/samba/smb.conf
--- /etc/samba/smb.conf.org     2018-05-02 18:16:25.567600455 +0900
+++ /etc/samba/smb.conf 2018-05-02 18:20:40.762445925 +0900
@@ -190,13 +190,13 @@
 # Un-comment the following (and tweak the other settings below to suit)
 # to enable the default home directory shares. This will share each
 # user's home directory as \\server\username
-;[homes]
-;   comment = Home Directories
-;   browseable = no
+[homes]
+   comment = Home Directories
+   browseable = no

 # By default, the home directories are exported read-only. Change the
 # next parameter to 'no' if you want to be able to write to them.
-;   read only = yes
+   read only = no

 # File creation mask is set to 0700 for security reasons. If you want to
 # create files with group=rw permissions, set next parameter to 0775.
@@ -211,7 +211,7 @@
 # Un-comment the following parameter to make sure that only "username"
 # can connect to \\server\username
 # This might need tweaking when using external authentication schemes
-;   valid users = %S
+   valid users = %S

 # Un-comment the following and create the netlogon directory for Domain Logons
 # (you need to configure Samba to act as a domain controller too.)
```

## Ubuntuからアクセスする方法（Ubuntuがクライアントの場合）
```bash
sudo apt-get install -y cifs-utils
sudo mkdir /mnt/XXX
```
`XXX` は任意

### マウント
```bash
sudo mount.cifs //AAA.AAA.AAA.AAA/BBB /mnt/XXX/ -o username=BBB,uid=$(id -u),gid=$(id -g)
```
`AAA` : サーバIP  
`BBB` : サーバ側のユーザ名

### アンマウント
```bash
sudo umount /mnt/XXX
```
