# Samba CentOS 6

```bash
sudo yum install -y samba
sudo chmod 755 /home/$USER
sudo smbpasswd -a $USER
sudo cp -a /etc/samba/smb.conf /etc/samba/smb.conf.org
sudo vi /etc/samba/smb.conf # 編集方法は以下
sudo /etc/rc.d/init.d/smb start
sudo /etc/rc.d/init.d/nmb start
sudo chkconfig smb on
sudo chkconfig nmb on
sudo setsebool -P samba_export_all_rw 1
sudo /etc/rc.d/init.d/iptables stop
sudo chkconfig iptables off
sudo chkconfig ip6tables off
```

### /etc/samba/smb.conf

L58-62
```text
### START ###
        unix charset = UTF-8
        dos charset = CP932
        display charset = UTF-8
### END ###
```

L79-82
```text
### START ###
#       workgroup = MYGROUP
        workgroup = WORKGROUP
### END ###
```

L89-91
```text
### START ###
        hosts allow = 127.0.0.1 10. 172.16. 192.168.
### END ###
```

L232-236
```text
### START ###
#       load printers = yes
        load printers = no
        disable spoolss = yes
### END ###
```

L267-270
```text
### START ###
        create mask = 644
        directory mask = 755
### END ###
```


