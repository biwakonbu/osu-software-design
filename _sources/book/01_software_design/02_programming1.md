# 第 2 回 プログラミング基礎 1

プログラミング言語 Python の基礎構文を学びます。変数、制御構文、関数、クラスを学びます。

## 学び始めに

本資料ではプログラムの一部分のみを記述したり、全てを記述したり様々な表現を行ないます。  
ファイル名が記載されている場合は、丸々動作するものとして、ファイル名が記載されていない場合は一部分の記載と思ってください。

また、一部分の場合でも実行できるプログラムである場合はありますし、単純にコピーだけでは動作しない場合でもどうすれば動作するかを考えて自分で動作を確認するようにしてください。

また、インタープリタで実行する場合の記法には慣れてください。

```
> 'Hello World!'
Hello World!
```

上記のように、`>` が行頭に記載されている場合はインタープリタでの実行を前提にしています。  
その場合、次の行に記載されている文字列は一行前の実行結果 (戻り値) となります。


## 変数

よくあるプログラミングを始める時の定番のプログラムがあります。


``` python
print('Hello World!')
```

このプログラムを実行すると、ターミナルに Hello World! と出力されます。  
このプログラムは print 関数と 'Hello World!' という文字列から構成されています。

もし、下記のような出力を作りたい場合、どうするかを考えてみます。

```
Hello World!
Hello World!
Hello World!
```

この出力を作るプログラムは単純に考えれば下記のようになります。

``` python
print('Hello World!')
print('Hello World!')
print('Hello World!')
```

プログラムが 3 行畫かれています。プログラムが複数行畫かれている時の読み方は、1 番上から順番に 1 行ずつ読んでいく事です。特殊な場合だけこの規則と異なる読み方をする事になりますが、それは都度説明するので今は上から読むとだけ覚えてください。

今回の要件では、出力が一緒であれば良いため、このプログラムでも問題はありません。  
ただ、もし `World!` の部分を `Japan` に変更したい場合は 3 箇所変更する必要がでてきます。

次のように変数を利用すれば、1 箇所変更するのみで全ての実行内容を変更する事が可能になります。

``` python
hello = 'Hello world!'

print(hello)
print(hello)
print(hello)
```

```
Hello World!
Hello World!
Hello World!
```

変数はプログラムに状態を記憶させる事ができるため、定義した内容を何度も再利用する事ができます。  
これは変数を使うメリットです。変数を使わない場合は全て直接記述する必要があり、変更したい部分を全て修正しないといけないのは非常に不便です。

こういった色々な部分に同じ内容を記載している場合に変数などを利用してまとめる事を「共通化」と言います。  
共通化はプログラミングにおいて読み易いプログラムや、バグの少ないプログラムを畫くために重要な考え方なので意識するようにしましょう。

また、変数の使い方は共通化だけではなく、先程でてきた「記憶」させる事も重要な使い方となります。

``` python
count = 0
count += 1
count += 1
count += 1
count += 1
count += 1
count += 1
print(sum)
```

```
6
```

少しチープなプログラムですが数を 1 つずつ数え上げていくプログラムを書いてみました。  
変数を使わない場合、このような書き方はできません。

直接 `6` を print に与え、表示する事はできますが、プログラムが計算していく事によって結果的に計算した数を出すという事が不可能だという話です。

後ででてくる制御構文や関数、クラスを組み合わせる事でどのように利用していくのか、イメージできるようになります。

## 制御構文

制御構文とは、プログラムを制御するための構文の事をさします。

Python では条件分岐は if 文、繰り返しは for 文か while 文を利用します。

### 条件分岐

条件分岐である if 文は下記のように利用します。

``` python
if 1 == 1:
  print('1 == 1 は True です')
```

上記の if 文は 1 が 1 と等価であるという意味です。この条件が真 (Python の真は True) である時に `print('1 == 1 は True です')` を実行する事になります。

`if 1 == 1:` が if 文の条件部分になります。

`if ` if の後のスペースは必ず半角にしてください。プログラム中のスペース (空白文字) は全て半角である必要があります。全角が許されるのは文字列の中 (' とか " で挟んでいる文字のこと) の場合のみとなります。  
また、条件文の記述の終わりを示すのは `:` コロンです。

`:` は文の区切りに使われるため、今後も頻繁に使います。

`if ` `:` の間に記述されている `1 == 1` は式となります。この式の結果が `True` or `False` で判断されます。  
この式というものが評価 (計算) されると bool で表現されます (`True` or `False`)。

`==` は比較演算子といい、左辺と右辺が等価であるかを評価します。つまり `1 == 1` は、1 は 1 と同じ値か? という意味になります。  
1 は 1 であるため、結果は真 (`True`) になります。もし、左辺か右辺が 2 だった場合 `1 == 2` とかだと 1 は 2 ではないため、`False` になります。

条件式が `False` になった場合、その条件分岐の中には入らず無視されます。  
今回のプログラムでいえば、`print('1 == 1 は Trueです')` が実行されず、無視されるという事です。

:::{note}
`print` の位置がちょっとずれているように記載されていますが、これは間違いではありません。  
Python のプログラムでは、文と呼ばれるものは繋りを示す方法として、インデント (字下げ) という方法を用いています。  
インデントは、プログラムの行の開始位置を後ろに下げる事をいいます。  
半角スペースかタブ文字でインデントを付ける事ができますが、インデントに使う事ができる文字と文字数はプログラムの中で最初に使ったもので統一する必要があるため、自分の中でルールを決めて畫く事をオススメします。  
私のオススメはスペース 2 個です。
:::

もし無視されず、必ず何か処理をしたいと思う場合にももちろん対応できます。

``` python
if 1 == 1:
  print('1 == 1 は True です')
else:
  print('1 == 1 は False です')
```

`else:` を追加しました。`else` は全ての条件にあてはまるという意味になります。  
そのため、`if` で記述した条件が `True` にならなかった場合、次の行、次の行と条件を確認していき、`else` が登場するまで `True` にならなかった場合、`else` の内容が実行される事になります。

ただ、今回の条件の場合は `1 == 1` のため条件が `False` にならない為、何度実行しても `else` は実行されません。動作確認のために `False` になる条件に変えてみます。

``` python
if 1 == 2:
  print('1 == 1 は True です')
else:
  print('1 == 2 は False です')
```

実際にこのような条件式を畫く事はありませんが、実験で書いてみました。  
このプログラムを実行すると、`1 == 2 は False です` と表示されます。

2 パターンしか分岐できないのは不便なので、当然もっと細かく制御できます。  
`if` ~ `else` までの間に、`elif` を利用する事で、細かく分岐を作る事が可能です。

ついでに、`if` の時の条件制御が固定の値で続いているので梃 (てこ) 入れします。

``` python
num = input('数字 1 ~ 3 のどれかを入力してください：')

if num == '1':
  print('入力された数字は 1 です')
elif num == '2':
  print('入力された数字は 2 です')
elif num == '3':
  print('入力された数字は 3 です')
else:
  print('求めている数字が入力されませんでした')
```

:::{note}
input() は input 関数といい、プログラムを実行した際に入力を受け付ける関数です。
引数に与えた文字列がある場合、入力を求める際に与えた文字列が出力されます。
要するに、どんな入力をして欲しいのか、先に問い掛けを表示できるという訳です。
:::

input を使用して num 変数が固定されない状況ができました。ついに変数が活用されて、if 文が活きてきます。

今回は `elif` によって条件とその際の処理を追加しました。ただ、少し今までとの違いに気付いて欲しいのですが、数字の比較が少し変わっています。

左辺が変数になったのは数字の変わりに変数をおいたので理解できますが、右辺が `'1'` のように文字として扱われています。これは、`input` によって入力された内容が全て文字列になるからです。

そのため、input の結果を数値に変換して num に代入するか、比較する際に数値ではなく、文字として比較する必要があります。注意してください。
