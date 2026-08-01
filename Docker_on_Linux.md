# Docker on Linux

## Git
```bash
sudo apt-get update
sudo apt-get install git
```

## Docker

### Set up Docker's apt repository.
```sh
# Add Docker's official GPG key:
sudo apt update
sudo apt install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
```

### Install the Docker packages.

```sh
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Docker が稼働しているか確認
```sh
sudo systemctl status docker
```

Docker が稼働していない場合は以下を実行
```sh
sudo systemctl status docker
```

参考: https://docs.docker.com/engine/install/ubuntu/

## 自ユーザにdocker権限を付加
```bash
sudo usermod -aG docker $USER
exit # 一度ログアウトしてから再ログイン
```

## Docker compose
以下のURLから最新の正式版をダウンロード  
`#{x.y.z}` は最新の正式版のバージョンに差し替え  
https://github.com/docker/compose/releases/
```bash
sudo curl -o /usr/local/bin/docker-compose -L https://github.com/docker/compose/releases/download/v#{x.y.z}/docker-compose-`uname -s`-`uname -m`
sudo chmod 755 /usr/local/bin/docker-compose
```

## Direnv
以下のURLから最新の正式版をダウンロード  
`#{x.y.z}` は最新の正式版のバージョンに差し替え  
https://github.com/direnv/direnv/releases
```bash
sudo curl -o /usr/local/bin/direnv -L https://github.com/direnv/direnv/releases/download/v#{x.y.z}/direnv.linux-amd64
sudo chmod 755 /usr/local/bin/direnv
```

* BASHユーザは~/.bashrcに以下を追加
```bash
eval "$(direnv hook bash)"
```
* ZSHユーザは~/.zshrcに以下を追加
```bash
eval "$(direnv hook zsh)"
```
