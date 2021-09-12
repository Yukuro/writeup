# YUUGEN
とあるアニメのファンである都久志くんはそのアニメのコラボ列車を人目見ようと駅に向かった。しかし、駅は密状態だったため駅構内に入るのを諦めて、駅の外から見ることにしたのであった。

[YUUGEN.mp4](images/YUUGEN.mp4)

- **この問題は10回までしか提出できません。**
- 駅名は[JR線 駅ナンバリング路線図](http://www.jrkyushu.co.jp/news/__icsFiles/afieldfile/2018/09/28/Newsrelease-ekinumbering.pdf)内に記載されている駅名の英語表記を使用します。
- 駅名がそのままフラグになります。仮に駅名が`Kyoto`の場合、フラグは `TsukuCTF{Kyoto}` となります

## Solution
とある路線をSLが走っている映像が提供される。

SLの先頭に「無限」マークがあったので、検索すると「鬼滅の刃 無限列車編」とコラボしたSLだとわかる。

検索すると、[「SL鬼滅の刃」追加運航決定！](https://www.jrkyushu.co.jp/news/__icsFiles/afieldfile/2020/12/11/201211_slkimetsu_tsuikaunkou.pdf)のような文書を発見した。どうやら熊本～博多を走行するらしい。

映像を見ると
- 新幹線らしき高架と地上の路線が交差している地点であること
- そこまで田舎ではないこと
がわかるので、それをもとにGoogleマップやストリートビューで検索すると竹下駅周辺であることがわかる

`TsukuCTF{Takeshita}`