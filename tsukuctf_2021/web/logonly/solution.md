# logonly
Tsukushiくんの悪友のスクリプトキディSuginaくんはTsukushiくんのサーバをハッキングしたようです。残念なことにTsukushiくんはサーバのログを標準出力で取っていただけでした。Suginaくんは次のようなメッセージを送ってきました。
```
Tsukushiくんへ

君のサーバをハッキングしました。
Kali Linuxの中のツールとファイルを使ったらrootで簡単にログインできたけど大丈夫ですか？

Suginaより
```
添付のログを見てTsukushiくんのパスワードを教えてください。

※パスワードがそのままフラグになります。仮にパスワードがpassの場合、フラグはTsukuCTF{pass}となります。

[logonly](files/logonly)

## Solution
標準出力で受け取っていたというサーバのログを渡される。

ログを見ると214153回目の試行までは`[11/Sep/2021 12:00:00] "POST / HTTP/1.1" 401 -`で、214154回目の試行でログインに成功したとわかる。

また、問題文より「Kali Linuxのツールとファイルを使った」とあるので、Kali Linux内部のツールでパスワードリストを作って総当たりしたものと考えられる。

Kali Linuxのツール かつ パスワードリストが用意されている かつ 214154個以上のパスワードを用意してあることを念頭に調べていくと、[RockYou.txt](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt)が引っかかったので、この214154行目のパスワードをフラグにすると通すことができた。