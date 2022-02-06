# Docker on Linux
## Ubuntu
### Git
```bash
sudo apt-get update
sudo apt-get install git
```

### Docker
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get -y install docker-ce
sudo vi /etc/docker/daemon.json # 編集方法は下記参照
sudo systemctl restart docker.service
```

#### /etc/docker/daemon.json
```json
{
  "experimental": true
}
```
`One of the configured repositories failed` というエラーが出てビルドが失敗する場合は、
以下コマンドで出力されるIPを、 `dns` をキーにして配列で記載
```bash
nmcli dev show | grep 'IP4.DNS'
```

#### 例
```bash
$ nmcli dev show | grep 'IP4.DNS'
IP4.DNS[1]:                             192.168.3.11
IP4.DNS[2]:                             8.8.8.8
```
/etc/docker/daemon.json の中身
```json
{
  "experimental": true,
  "dns": ["192.168.3.11", "8.8.8.8"]
}
```

参考： https://askubuntu.com/questions/475764/docker-io-dns-doesnt-work-its-trying-to-use-8-8-8-8

## CentOS
### Git
```bash
sudo yum install git -y
```
### Docker
```bash
sudo yum -y install yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce -y
sudo mkdir /etc/docker
sudo vi /etc/docker/daemon.json # 編集方法は下記参照
sudo systemctl start docker.service
sudo chkconfig docker on
```
#### /etc/docker/daemon.json
```json
{
  "experimental": true
}
```

## Linux共通
### 自ユーザにdocker権限を付加
```bash
sudo usermod -aG docker $USER
exit # 一度ログアウトしてから再ログイン
```

### Docker compose
以下のURLから最新の正式版をダウンロード  
`#{x.y.z}` は最新の正式版のバージョンに差し替え  
https://github.com/docker/compose/releases/
```bash
sudo curl -o /usr/local/bin/docker-compose -L https://github.com/docker/compose/releases/download/v#{x.y.z}/docker-compose-`uname -s`-`uname -m`
sudo chmod 755 /usr/local/bin/docker-compose
```

### Direnv
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
