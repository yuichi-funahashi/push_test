# VsCodeで図を描く（Mermaidを使用）
## ２つの拡張機能を導入する
- [MarkDown Preview Mermaid Support](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid)
- [Mermaid MarkDown Syntax Highlighting](https://marketplace.visualstudio.com/items?itemName=bpruitt-goddard.mermaid-markdown-syntax-highlighting)
---
## フローチャート
```mermaid
graph TD
  A --> B;
	A --> C;
	B --> D;
	C --> D;
```
---
## シーケンス図
```mermaid
sequenceDiagram
    participant 太郎
    participant 花子
    太郎->>花子: こんにちは、花子さん。元気ですか？
    loop Healthcheck
        花子->>花子: Fight against hypochondria
    end
    Note right of 花子: Rational thoughts <br/>prevail!
    花子-->>太郎: 良いですよ！
    花子->>次郎: あなたはどうですか？
    次郎-->>花子: とても良いです
```
---
## ガントチャート
```mermaid
gantt
dateFormat  YYYY-MM-DD
title ガントチャートのサンプル
    excludes weekdays 2014-01-10

section A section
    完了したタスク            :done,    des1, 2022-07-06,2022-07-08
    アクティブなタスク        :active,  des2, 2022-07-09, 3d
    未来のタスク              :         des3, after des2, 5d
    別な未来のタスク          :         des4, after des3, 5d
```
---
## クラス図
```mermaid
classDiagram
Class01 <|-- AveryLongClass : Cool
Class03 *-- Class04
Class05 o-- Class06
Class07 .. Class08
Class09 --> C2 : Where am i?
Class09 --* C3
Class09 --|> Class07
Class07 : equals()
Class07 : Object[] elementData
Class01 : size()
Class01 : int chimp
Class01 : int gorilla
Class08 <--> C2: Cool label
```
---
## Gitグラフ
```mermaid
gitGraph
       commit
       commit
       branch develop
       commit
       commit
       commit
       checkout main
       commit
       commit
```
---
## ER図
```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    CUSTOMER }|..|{ DELIVERY-ADDRESS : uses
```
---
## ユニジャージー図
```mermaid
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me
```
---
## ステータス図（縦）
```mermaid
stateDiagram-v2
    state if_state <<choice>>
    [*] --> IsPositive
    IsPositive --> if_state
    if_state --> False: if n < 0
    if_state --> True : if n >= 0

    [*] --> Still
    Still --> [*]
%% this is a comment
    Still --> Moving
    Moving --> Still %% another comment
    Moving --> Crash
    Crash --> [*]
```
## ステータス図（横）
```mermaid
stateDiagram
    direction LR
    [*] --> A
    A --> B
    B --> C
    state B {
      direction LR
      a --> b
    }
    B --> D
```
---
## 円グラフ
```mermaid
pie showData
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
```
---
## 要件図
```mermaid
    requirementDiagram

        requirement test_req {
        id: 1
        text: the test text.
        risk: high
        verifymethod: test
        }

        element test_entity {
        type: simulation
        }

        test_entity - satisfies -> test_req
```
---
## XYチャート
```mermaid
    xychart-beta
        title "Sales Revenue"
        x-axis [jan, feb, mar, apr, may, jun, jul, aug, sep, oct, nov, dec]
        y-axis "Revenue (in $)" 4000 --> 11000
        bar [5000, 6000, 7500, 8200, 9500, 10500, 11000, 10200, 9200, 8500, 7000, 6000]
        line [5000, 6000, 7500, 8200, 9500, 10500, 11000, 10200, 9200, 8500, 7000, 6000]
```
---
## 象限チャート
```mermaid
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A: [0.3, 0.6]
    Campaign B: [0.45, 0.23]
    Campaign C: [0.57, 0.69]
    Campaign D: [0.78, 0.34]
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
```
# Pythonでグラフを描く
```python {cmd=true matplotlib=true}
import numpy as np
import japanize_matplotlib
import matplotlib.pyplot as plt
japanize_matplotlib.japanize()

# 三点から係数a, b, c を求める
xx = [1,2,3]
yy = [2,5,10]

A = np.array([[xx[0]**2, xx[0], 1], [xx[1]**2, xx[1], 1], [xx[2]**2, xx[2], 1]])
b = np.array([yy[0], yy[1], yy[2]])
a,b,c = np.linalg.solve(A,b)

# グラフに描画する
x = np.linspace(0.5 ,4.5 ,100)
y = a * x**2 + b * x + c

plt.plot(x,y)
plt.plot(xx,yy,'o')
plt.title("二次関数 y=ax^2+bx+c")
plt.xlabel("x")
plt.ylabel("y")
plt.show()
```
```python {cmd=true matplotlib=true}
import numpy as np
import japanize_matplotlib
import matplotlib.pyplot as plt
japanize_matplotlib.japanize()


# 平均10、標準偏差10 の正規乱数を100件生成
x = np.random.normal(10, 10, 1000)

plt.hist(x)
# ヒストグラムを表示
plt.show()
```
```python {cmd=true matplotlib=true}
# アステロイド 曲 線 を 描 く Python の プログ ラム コード の 例

import numpy as np # numpy ライブ ラリー を インポート する
import japanize_matplotlib
import matplotlib.pyplot as plt
japanize_matplotlib.japanize()

# パラメータ の 設定
a = 1 # 楕円 の 半径
t = np.linspace(0, 2 * np.pi, 100) # 角 度 の 配列

# x 座標 と y 座標 の 配列 を 計算 する
x = a * np.cos(t) ** 3
y = a * np.sin(t) ** 3

# アステロイド 曲 線 を 描画 する
plt.plot(x, y)
plt.xlabel("x")
plt.ylabel("y")
plt.title("アステロイド曲線")
plt.axis("equal")
plt.show()
```
```gnuplot {cmd=true output="html"}
set terminal svg
set isosamples 50,50
set hidden3d
splot x**2+y**2
splot sin(x)*cos(y)
set key below
set samples 500
set zeroaxis
set yrange [-2.1:2.1]
plot [-100:100] sin(x + 0.05*x) + sin(x - 0.05*x)
reset
set grid
set xlabel "軌道長半径 a"
set ylabel "公転周期 T"
plot "planets.dat" using 2:3 pt 7 lc 7 ps 0.7 notitle
set logscale xy
replot
f(x) = K*x**p
fit f(x) "planets.dat" using 2:3 via K,p
replot f(x)
```
![波動](hadou.gif)