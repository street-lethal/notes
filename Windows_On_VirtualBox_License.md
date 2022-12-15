# Windows on VirtualBox License

```sh
sudo cat /sys/firmware/acpi/tables/MSDM > /mnt/Data/VirtualBox_VMs/Windows10/msdm
VBoxManage setextradata Windows10 "VBoxInternal/Devices/acpi/0/Config/CustomTable" "/mnt/Data/VirtualBox_VMs/Windows10/msdm"
```
