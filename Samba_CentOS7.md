# Samba CentOS 7

```bash
sudo yum install -y samba
sudo chmod 755 /home/$USER
sudo smbpasswd -a $USER
sudo cp -a /etc/samba/smb.conf /etc/samba/smb.conf.org
sudo cp /etc/samba/smb.conf.example /etc/samba/smb.conf
sudo vi /etc/samba/smb.conf # 編集方法は以下
sudo systemctl enable smb.service
sudo systemctl enable nmb.service
sudo systemctl restart smb.service
sudo systemctl restart nmb.service
sudo setsebool -P samba_export_all_rw 1
sudo systemctl stop firewalld
```


### /etc/samba/smb.conf

[global] の下
```text
unix charset = UTF-8
dos charset = CP932
display charset = UTF-8
```

```text
; workgroup = MYGROUP
workgroup = WORKGROUP
```

```text
; hosts allow = 127. 192.168.12. 192.168.13.
  hosts allow = 127.0.0.1 10. 172.16. 192.168.
```

```text
; load printers = yes
load printers = no
disable spoolss = yes
```
valid users = MYDOMAIN\%S  の下
```text
create mask = 644
directory mask = 755
```