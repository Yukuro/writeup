# PCB
筑紫くん「素日華の誕生日プレゼントに彼女の好きな星座を基板に入れたけど気づいてくれるかな～」
フラグは星座を表す英単語大文字で答えてください。例えば星座が仔犬座の場合はTsukuCTF{CANIS MINOR}、獅子座の場合はTsukuCTF{LEO}となります。

※この問題は基盤設計ソフトが手元ない場合でも解くことが可能です。

## Solution
ガーバーデータが渡されるので、[Online Gerber Viewer](https://www.pcbway.com/project/OnlineGerberViewer.html)に通す。

通すと`layers`のところに星座っぽいものが現れるので、それを検索する。
なお、`Power`と記載してあるところを考慮すると星座がヒットしなかったので、考慮せずに検索するとはくちょう座が出てきた。
よってこれをフラグにする。

`TsukuCTF{CYGNUS}`