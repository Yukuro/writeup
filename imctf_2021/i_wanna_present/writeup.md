# i wanna present🎁
今夜はクリスマスイブ。ちゃんと貰えるように下準備をしておこう。いい子にしていたら貰えるって！ちゃんと準備が出来る子だもん。

### Solution
gitでごにょごにょした形跡のあるファイル一式が配られる

app.pyのhistoryを詳しく見ていくと、`/big-sock`にPOSTした際に`present`が`.env`と等しい場合に`flag.txt`の中身を返すらしい

また、`.env`のhistoryを詳しく見ていくと、中身は`Talking_Turboman_Figure`

なので、Postmanを使って`104.196.236.136:12025/big-sock`に`{"present":"Talking_Turboman_Figure"}`をPOSTした

レスポンスとして、`correct`の文字とともにBase64エンコードされたflagが返ってくる

`imctf{Jin913_A11_7h3_Way}`