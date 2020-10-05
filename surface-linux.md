## Enable Wifi

https://github.com/linux-surface/linux-surface/wiki/Installation-and-Setup

## Enable scrolling on Firefox

```sh
sudo vi /usr/share/applications/firefox.desktop
```

Find the `Exec` line in the `[Desktop Entry]` section (which was L153 on Ubuntu 20.04), and change it to

```
Exec=env MOZ_USE_XINPUT2=1 firefox %u
```

then reboot.
