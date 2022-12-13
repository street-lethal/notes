# やる事

```sh
sudo apt install -y virtualbox-dkms --reinstall
```

* パスワード設定を求められるので8文字以上16文字以下で設定する
* 再起動後、 "Enroll MOK" を選択し、設定したパスワードを入力する

## 実際にコンソールに表示されるメッセージ

```
 ┌──────────────────────────────────────────────────────────────────────────────┤ Configuring Secure Boot ├───────────────────────────────────────────────────────────────────────────────┐
 │                                                                                                                                                                                        │ 
 │ Your system has UEFI Secure Boot enabled.                                                                                                                                              │ 
 │                                                                                                                                                                                        │ 
 │ UEFI Secure Boot requires additional configuration to work with third-party drivers.                                                                                                   │ 
 │                                                                                                                                                                                        │ 
 │ The system will assist you in configuring UEFI Secure Boot. To permit the use of third-party drivers, a new Machine-Owner Key (MOK) has been generated. This key now needs to be       │ 
 │ enrolled in your system's firmware.                                                                                                                                                    │ 
 │                                                                                                                                                                                        │ 
 │ To ensure that this change is being made by you as an authorized user, and not by an attacker, you must choose a password now and then confirm the change after reboot using the same  │ 
 │ password, in both the "Enroll MOK" and "Change Secure Boot state" menus that will be presented to you when this system reboots.                                                        │ 
 │                                                                                                                                                                                        │ 
 │ If you proceed but do not confirm the password upon reboot, Ubuntu will still be able to boot on your system but any hardware that requires third-party drivers to work correctly may  │ 
 │ not be usable.                                                                                                                                                                         │ 
 │                                                                                                                                                                                        │ 
 │                                                                                         <了解>                                                                                         │ 
 │                                                                                                                                                                                        │ 
 └────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┘ 
```

```
                                                        ┌────────────────────────┤ Configuring Secure Boot ├────────────────────────┐
                                                        │                                                                           │ 
                                                        │                                                                           │ 
                                                        │ Enter a password for Secure Boot. It will be asked again after a reboot.  │ 
                                                        │                                                                           │ 
                                                        │ _________________________________________________________________________ │ 
                                                        │                                                                           │ 
                                                        │                    <了解>                      <取消>                     │ 
                                                        │                                                                           │ 
                                                        └───────────────────────────────────────────────────────────────────────────┘ 
```

```
                                                          ┌──────────────────────┤ Configuring Secure Boot ├──────────────────────┐
                                                          │                                                                       │ 
                                                          │                                                                       │ 
                                                          │ Enter the same password again to verify you have typed it correctly.  │ 
                                                          │                                                                       │ 
                                                          │ _____________________________________________________________________ │ 
                                                          │                                                                       │ 
                                                          │                  <了解>                    <取消>                     │ 
                                                          │                                                                       │ 
                                                          └───────────────────────────────────────────────────────────────────────┘ 
```