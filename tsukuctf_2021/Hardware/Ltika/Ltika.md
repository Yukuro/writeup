# Ltika
Tsukushiくんはシリアル通信等メッセージを送ることに飽きてしまったため、Lチカ（LEDを光らせること）でメッセージを伝える方法を考案した。メッセージを（ローマ字(大文字)、数字、記号を含む）フラグ形式で答えてください。例えばメッセージがTSUKUSHI123&の場合、フラグはTsukuCTF{TSUKUSHI123&}となります。

※この問題はマイコンが手元にない場合でも解くことが可能です。（Tinkercadを使ったardunioのシミュレータも使用可）

## Solution
Aruduinoのソースコードが渡されるのでそれを読み解く。

`blinking()`関数が短点、`lit()`関数が長音を表しているので、[Morse Code Translator](https://morsecode.world/international/translator.html)を使用して、フラグを入手した

