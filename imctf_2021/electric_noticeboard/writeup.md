# electric noticeboard
今日はクリスマス。彼女のためにサプライズで電光掲示板メッセージを流すことにした。商店街の人に「電光掲示板を動かすプログラム」を渡した。電光掲示板には A-2308SR と atmega328 が使われているようだ。

### Solution
Arduinoのプログラムが渡される
問題文のリンクから、16セグメントLEDのデータシートも見える

Arduinoのプログラムから、データシート2枚目の表示にしたがって表示しようとしているのがわかる。
まずは、Arduinoのプログラムの`TurnOn`で光らせている信号とデータシート上の表記を対応させたかったので、以下のプログラムを書いた
```python
data = [[False, False, False, False, False, False, False, False, False, False, False, False, False, False, True, False, False],[False, False, False, True, False, False, True, False, True, True, False, False, False, False, True, False, False],[False, False, False, False, True, False, True, False, True, False, False, False, False, False, False, False, False],[False, False, False, False, False, False, False, False, True, True, False, True, False, False, True, False, False],[False, True,False, False, False, False, False, False, True, True, False, True, False, False, True, False, False],[False, True,False, False, False, True, False, False, True, False, False, True, False, False, True, False, False],[False, False, False, True, False, False, True, False, False, False, False, False, False, True, False, True, False],[False, False, False, False, True, True, True, False, True, False, False, False, False, False, False, True, False],[False, False, False, False, True, True, False, False, False, False, False, False, False, False, False, False, False],[False, False, False, True, False, False, True, False, False, False, False, False, False, True, False, True, False],[False, False, False, False, False, False, False, False, False, False, False, False, False, False, True, False, False],[False, False, False, False, False, False, False, False, False, False, False, True, False, False, True, False, False],[False, False, False, False, False, False, False, False, False, False, False, True, False, False, True, False, False],[False, False, False, False, True, True, False, False, False, False, False, False, False, False, False, False, False],[False, False, False, False, True, False, True, False, True, False, False, False, False, False, False, False, False],[False, False, False, False, True, False, True, False, True, False, False, False, False, False, True, False, False],[False, False, False, False, False, False, True, False, True, False, False, False, False, False, True, False, False],[False, False, False, False, False, False, False, False, True, True, False, True, False, False, True, False, False],[False, False, False, False, False, False, False, False, False, False, False, False, False, False, True, False, False],[False, False, False, False, False, False, True, False, True, False, False, False, False, False, True, False, False],[False, False, False, False, True, False, True, False, False, False, False, False, False, False, True, False, False],[False, False, False, False, True, True, True, False, True, False, False, False, False, False, False, True, False],[False, False, False, False, True, True, False, False, False, False, False, False, False, False, False, False, False],[False, False, False, False, False, False, False, False, True, True, False, True, False, False, True, False, False],[False, False, False, False, True, False, True, False, True, False, False, False, False, False, True, False, False],[False, False, False, False, True, True, False, False, False, False, False, False, False, False, False, False, False],[False, False, False, False, True, False, True, True, True, False, False, False, False, False, True, False, False],[False, False, False, False, True, True, True, False, True, False, False, False, False, False, False, True, False],[False, False, False, False, True, True, False, False, False, False, False, False, False, False, False, False, False],[False, False, False, False, False, False, False, False, True, True, False, True, False, False, True, False, False],[False, False, False, False, True, False, True, False, True, False, False, False, False, False, True, False, False],[True, False, False, False, True, False, False, True, True, False, False, True, False, False, True, False, False],[False, False, False, False, True, True, True, False, True, False, False, False, False, False, False, True, False],[False, False, False, False, False, False, False, False, True, True, False, True, False, False, True, False, False],[False, False, False, False, False, False, True, True, True, False, False, False, False, False, True, False, False],[False, False, False, False, True, True, True, False, True, False, False, False, False, False, False, True, False],[False, False, False, False, False, False, True, False, True, False, False, False, False, False, False, False, False],[True, False, False, False, True, False, False, False, False, True, False, True, False, False, True, False, False]]
order = ["A1", "A2", "B", "C", "D1", "D2", "E", "F", "G1", "G2", "J", "K", "L", "M", "N", "P", "DP"]

for i, line in enumerate(data):
    print(str(i+1) + " ", end="")
    for j, l in enumerate(line):
        if l == True:
            print(order[j] + "", end='')
    print()
```

```bash
1 N
2 CEG1G2N
3 D1EG1
4 G1G2KN
5 A2G1G2KN
6 A2D2G1KN
7 CEMP
8 D1D2EG1P
9 D1D2
10 CEMP
11 N
12 KN
13 KN
14 D1D2
15 D1EG1
16 D1EG1N
17 EG1N
18 G1G2KN
19 N
20 EG1N
21 D1EN
22 D1D2EG1P
23 D1D2
24 G1G2KN
25 D1EG1N
26 D1D2
27 D1EFG1N
28 D1D2EG1P
29 D1D2
30 G1G2KN
31 D1EG1N
32 A1D1FG1KN
33 D1D2EG1P
34 G1G2KN
35 EFG1N
36 D1D2EG1P
37 EG1
38 A1D1G2KN
```

`16 segment display simulator`とかでググると
https://www.geocachingtoolbox.com/index.php?lang=en&page=segmentDisplay
が出てきたので、これに一文字一文字コピペしていく

地道に作業をして以下のような画像を得た
![](./flag.png)

`imctf{we_will_continue_to_be_together}`