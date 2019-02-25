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
* 差分が以下のようになるよう修正する
```bash
[admin@localhost ~]$ diff -uprN /etc/samba/smb.conf.example /etc/samba/smb.conf
--- /etc/samba/smb.conf.example 2017-11-28 01:21:52.000000000 +0900
+++ /etc/samba/smb.conf 2018-05-02 20:50:00.157765018 +0900
@@ -60,6 +60,9 @@
 #======================= Global Settings =====================================

 [global]
+unix charset = UTF-8
+dos charset = CP932
+display charset = UTF-8

 # ----------------------- Network-Related Options -------------------------
 #
@@ -81,13 +84,13 @@
 # hosts deny = the hosts not allowed to connect. This option can also be used on
 # a per-share basis.
 #
-       workgroup = MYGROUP
+       workgroup = WORKGROUP
        server string = Samba Server Version %v

 ;      netbios name = MYSERVER

 ;      interfaces = lo eth0 192.168.12.2/24 192.168.13.2/24
-;      hosts allow = 127. 192.168.12. 192.168.13.
+       hosts allow = 127.0.0.1 10. 172.16. 192.168.

 # --------------------------- Logging Options -----------------------------
 #
@@ -244,7 +247,8 @@
 # printcap name = used to specify an alternative printcap file.
 #

-       load printers = yes
+       load printers = no
+       disable spoolss = yes
        cups options = raw

 ;      printcap name = /etc/printcap
@@ -278,6 +282,8 @@
        writable = yes
 ;      valid users = %S
 ;      valid users = MYDOMAIN\%S
+       create mask = 644
+       directory mask = 755

 [printers]
        comment = All Printers
```