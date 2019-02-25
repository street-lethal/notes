# Samba Ubuntu

```bash
sudo apt-get install -y samba
sudo pdbedit -a $USER
sudo cp -a /etc/samba/smb.conf /etc/samba/smb.conf.org
sudo vi /etc/samba/smb.conf # 編集方法は以下
sudo systemctl restart smbd
sudo systemctl restart nmbd
sudo ufw allow 137
sudo ufw allow 138
sudo ufw allow 139
sudo ufw allow 445
```

### /etc/samba/smb.conf
```text
;[homes]
;   comment = Home Directories
;   browseable = no
[homes]
   comment = Home Directories
   browseable = no
```

```text
;   read only = yes
   read only = no
```

```text
;   valid users = %S
   valid users = %S
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
