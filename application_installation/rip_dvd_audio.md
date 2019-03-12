# Rip DVD Audio
## transcode インストール
```bash
sudo apt install -y transcode
```
## チャプタ数確認
```bash
tcprobe -i /dev/sr0
```
以下のような行を探す。(この例ではチャプタ数は21)
```text
[dvd_reader.c] DVD title 1/1: 21 chapter(s), 1 angle(s), title set 1
```

## 変換
`21` の部分にはチャプタ数を入れる
```bash
for i in {1..21};do transcode -x null,dvd -y null,tcaud -i /dev/sr0 -T 1,$i,1 -a 0 -E 44100,16,2 --lame_preset medium -m ~/Music/`printf "%02d" $i`.mp3; done
```
