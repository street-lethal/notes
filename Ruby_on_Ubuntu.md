# Ruby on Ubuntu
## 各種パッケージのインストール
```bash
sudo apt update
sudo apt -y install git curl g++ make zlib1g-dev libssl-dev libreadline-dev libyaml-dev libxml2-dev libxslt-dev nodejs
```

以下は恐らく不要
```bash
# sudo apt -y install sqlite3 libsqlite3-dev
# sudo apt -y install postgresql postgresql-server-dev-all
# sudo apt -y install mysql-server mysql-client libmysqlclient-dev
```

## rbenv のインストール
```bash
cd
git clone git://github.com/sstephenson/rbenv.git .rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL
source ~/.bashrc
```

## ruby-build のインストール
```bash
mkdir -p ~/.rbenv/plugins
cd ~/.rbenv/plugins
git clone git://github.com/sstephenson/ruby-build.git
```

## ruby-update のインストール
```bash
git clone https://github.com/rkh/rbenv-update.git "$(rbenv root)/plugins/rbenv-update"
```

## ruby のインストール
```bash
rbenv install 2.5.0
rbenv global 2.5.0
```
