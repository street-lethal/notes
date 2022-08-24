# Go on Ubuntu

## Install

```sh
git clone https://github.com/syndbg/goenv.git ~/.goenv
echo 'export GOENV_ROOT="$HOME/.goenv"' >> ~/.bashrc 
echo 'export PATH="$GOENV_ROOT/bin:$PATH"' >> ~/.bashrc 
echo 'eval "$(goenv init -)"' >> ~/.bashrc 
source .bashrc 
goenv version
```

## set version

```sh
goenv install 1.19.0
goenv global 1.19.0
```

## List available versions

```shell
goenv install --list
```

https://github.com/syndbg/goenv/blob/master/INSTALL.md
