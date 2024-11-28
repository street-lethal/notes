# Go on Ubuntu

```shell
git clone https://github.com/go-nv/goenv.git ~/.goenv
```
```shell
echo 'export GOENV_ROOT="$HOME/.goenv"' >> ~/.bashrc
echo 'export PATH="$GOENV_ROOT/bin:$PATH"' >> ~/.bashrc
```
```shell
echo 'eval "$(goenv init -)"' >> ~/.bashrc
source ~/.bashrc
```
```shell
echo 'export PATH="$GOROOT/bin:$PATH"' >> ~/.bashrc
echo 'export PATH="$PATH:$GOPATH/bin"' >> ~/.bashrc
```
```shell
exec $SHELL
goenv install 1.23.3
goenv global 1.23.3
```


https://github.com/go-nv/goenv/blob/master/INSTALL.md
