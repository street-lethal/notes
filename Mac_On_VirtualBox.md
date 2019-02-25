# 事前設定
10.13.4

## Windows
コマンドプロンプトを管理者として実行
```
cd "C:\Program Files\Oracle\VirtualBox\"
VBoxManage.exe modifyvm "HighSierra" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
VBoxManage setextradata "HighSierra" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac11,3"
VBoxManage setextradata "HighSierra" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
VBoxManage setextradata "HighSierra" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"
VBoxManage setextradata "HighSierra" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
VBoxManage setextradata "HighSierra" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
```

### TIPS
テキストをコピーして ***.cmd ファイルとして保存し、.cmdファイルを管理者として実行すると楽

### 参考
https://drive.google.com/uc?id=1NCYqmwqgbt_PahzmVmiTtYw59lpArjV7&export=download


## Unix

```bash
cd
VBoxManage modifyvm "HighSierra_10_13_4"  --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
VBoxManage setextradata "HighSierra_10_13_4" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac11,3"
VBoxManage setextradata "HighSierra_10_13_4" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
VBoxManage setextradata "HighSierra_10_13_4" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"
VBoxManage setextradata "HighSierra_10_13_4" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
VBoxManage setextradata "HighSierra_10_13_4" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
```

### TIPS
実行ディレクトリはホームディレクトリでいけた。sudoなしでもいけた

### 参考
http://suzywu2014.github.io/ubuntu/2017/02/23/macos-sierra-virtualbox-vm-on-ubuntu

# VirtualBox 設定

* （言語選択）
* `ディスクユーティリティ`
  * `続ける`
* （左上の）`表示` -> `すべてのデバイスを表示`
  * `VBOX HARDDISK...` を選択
  * `消去`
    * `名前`： MacOSHighSierra
    * `消去`
    * `完了`
    * ウインドウを閉じる
* `macOSをインストール`
  * `続ける`
* `インストールを設定するには...` の画面で `続ける`
* `同意する`
  * `同意する`
* `MacOSHighSierra` を選択
  * `インストール`
* プログレスバーが100%になり、画面が戻ってきたらすぐ `F8` を押し続ける
* （BIOS的な画面が開く）
* `Boot Maintennance Manager`
  * `Boot From File`
  * 3つめ
  * `<macOS Install Data>`
  * `<Loced Files>`
  * `<Boot Files>`
  * `boot.efi`
* （黒画面が表示される）
* （再起動）
* （インストール中）
* （再起動）
* 国選択
* キーボード選択
* `転送しない`
* AppleID サインイン
* `同意する`
