## 日本語化

### 参考
* https://pc-freedom.net/basic/puppy-linux-bionicpub-8-0-japanese/
* https://pc-freedom.net/basic/puppy-linux-8-0-japanese-input/

## 言語パック導入
* [言語パック配布元](http://shinobar.server-on.net/puppy/opt/)より　`lang_pack_jp-2.1.sfs` をダウンロード
* `lang_pack_jp-2.1.sfs` 実行
* `[Install SFS]`
* `[Countrywizard Country Settings]` にチェックを入れて `[Run]`
  * 言語とキーボードを日本語に設定 して `[OK]`
* `[OK]`

## 日本語入力可能に
* メニューから `[セットアップ]` -> `[Puppy パッケージマネージャ]`  
  (注意) `[Puppy パッケージマネージャ]` というメニューがいくつか見えるが、アイコンに `+` が付いているもの 
* 検索窓に `[scim]` と入力して検索
* 一覧から `[scim-anthy_1.2.7-7]` をクリック
* `[Do it!]`
* `[OK]`

## Firefox インストール
[プログラム配布元](https://pkgs.org/download/firefox) よりダウンロード

## リマスタ
* メニューより `[セットアップ]` -> `[PuppyライブCDリマスタを実行]`
* `/tmp/root` が生成された段階で以下実行
  * `ll` 認識
    ```bash
    echo "alias ll='ls -l'" >> /tmp/root/.bashrc
    ```
  * Firefox
    ```bash
    cp -r ~/firefox /tmp/root/
    cp -r ~/.mozilla /tmp/root/
    ```
  * デスクトップに Firefox ショートカット作成  
    * (方法1)
      `/tmp/root/Choices/ROX-Filer/` をエディタで開き、4行目あたりに以下を追記する
      ```
        <icon x="100" y="410" label="firefox">/root/firefox/firefox</icon>
      ```
    * (方法2)
      ```bash
      cd /tmp/root/Choices/ROX-Filer/
      split -l 4 -d PuppyPin PuppyPin_split_
      echo '  <icon x="100" y="410" label="firefox">/root/firefox/firefox</icon>' >> PuppyPin_split_00
      cat PuppyPin_split_* > PuppyPin
      rm PuppyPin_split_* 
      ```
  * mpv設定
    ```
    echo '--loop' >> /tmp/root/.config/mpv/mpv.conf
    echo '--fs' >> /tmp/root/.config/mpv/mpv.conf
    ```


* `/tmp/etc` が生成された段階で以下実行
  * デフォルト言語を日本語にする  
    `/tmp/etc/profile` をエディタで開き `LANG=` から始まる行(95行目あたり)の `en_US` を `ja_JP` に書き換える 
      ```
      LANG=ja_JP.UTF-8
      ```
  * デフォルトキーボード設定を日本語にする  
    `/tmp/etc/X11/xorg.conf.udev` `XkbLayout` がある行(60行目あたり)の `us` を `jp` に書き換える
      ```
      Option      "XkbLayout" "jp" #xkeymap0
      ```

