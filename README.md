# Simple プログラミング言語
Simpleは子ども達が楽しくプログラミングしながらコンピュータの動作原理が学べる、新しい教育用プログラミング言語です。

実行方法はインタプリタ式でスクリプト実行のほかに、コンピュータに1回ずつ命令を出す対話的なREPLやデバッガも標準で備えています。
実行結果を表示する前に過程やロジックを示しているので、コンピュータの動作原理を学ぶことができます。

このSimpleの教育用プログラミング言語として普及を目指しています。

## 文法
Simpleは子どもでも分かりやすいようにRubyに似た平易な構文です。
スタックの仕組みを学ばせる為に計算方式は逆ポーランド記法を採用しています。
サンプルコードは[こちら](example.smp)でご覧いただけます。

### 変数と式
変数の型はすべて実数型で、変数を定義するには`var`文を使います。
文法は以下の通りです。
```
var 〔変数名〕=〔式〕
```
オペランドは変数と実数リテラルと関数の戻り値です。
基本的にオペランドは２つですが、否定は１つです。

論理演算では0がFalseでそれ以外はTrueとなります。
式は逆ポーランド記法で以下の演算子があります。
| 演算子 | 種類 | 意味 | 例 | 挙動 |
| :----:| :---: | :----: | :----- | :--|
| + | 算術| 足し算| 3 x + | 3とxを足す |
| - | 算術|引き算| x 2.6 - | xから2.6を引く |
| * | 算術|掛け算| 1.5 x * | 1.5とxを掛ける |
| / | 算術|割り算| 26 x / | 26をxで割る |
| % | 算術|割り算の余り| 72 x % | 72をxで割った余り |
| ^ | 算術|べき乗| x 2 ^ | xの2乗 |
| = | 比較|等しい| x 8.32 = | xは8.32と等しいか |
| & | 論理|AND| x y & | xかつyか |
| \| |論理|OR| x y \| | x又はyか | 
| > |比較|大きい| 7 x > | 7はxより大きいか |
| < |比較|小さい| 2 y < | 2はyより小さいか |
| ! |論理|否定| x ! | xの反対 |

### 制御構文
制御構文には条件分岐の`if`と繰り返しの`for`と`while`があります。
また、`exit`文で実行しているプロセスを終了できます。
#### 条件分岐
`if`文は条件に一致した時だけ実行します。
```
if〔条件式〕
  〔条件に一致した時の処理〕
end if
```
なお、一致しなかった場合の処理は`else`以降に書きます。
```
if〔条件式〕
  〔条件に一致した時の処理〕
else
  〔条件に一致しなかった場合の処理〕
end if
```
#### 繰り返し
`for`文は式の結果の数だけ繰り返します。
```
for〔式〕
  〔繰り返す処理〕
end for
```

`while`文は条件に一致している間繰り返します。
```
while 条件式
    繰り返す処理
end while
```
繰り返し処理において、`break`文でループから脱出できます。
```
if 脱出する条件
    break
end if
```
### 入出力
出力は`print`文を用います。
表示したい文字列や式をカンマ区切りで記述します。
文字列リテラルは`"`ダブルクォーテーションか`'`シングルクォーテーションで囲います。
```
print x ,'足す', y,"は", x y +,'です"
```

入力は`input`文を用います。変数に入力値が代入されます。
入力値は式として解釈され、その結果は変数に入ります。
```
input 変数名
```

### 関数
`func`文で関数を定義します。なお、戻り値を返すなら`return`文を用います。
```
func 関数名
    関数の行う処理
    return 戻り値
end func
```
`call`文に名まえを記述して関数を呼び出します。
```
call 関数名
```
式で戻り値を得たい場合は関数名に`（）`かっこを記述します。
```
var x = 3 関数名()　* 2 -
```
### 乱数
ランダムな値を得たい時は`rand`文を用います
```
rand ランダムな値を入れたい変数, 最小値, 最大値
```
## 実行
そのまま実行すると対話モードで起動します。
対話モードにはメモリの内容を表示する`mem`コマンドがあります。
`exit`コマンドで対話プログラミングを終了します。

デバッグやスクリプト実行がしたい場合は実行ファイルに続けて実行モードとファイル名を指定します。
実行モードを省略すると、スクリプト実行されます。
```
simple〔実行モード〕〔ファイル名〕
```
実行モードは以下の通りです。
| 実行モード名 | 省略名 | 挙動 |
| :---: | :---: | :--: |
| run | r |スクリプトモードで実行する |
| debug | d | デバッグモードで実行する |
| interactive| i | 対話モードで実行する |
### デバッグ
デバッガはファイルを一行ずつ実行します。デバッグメニューからデバッグコマンドを実行します。

`mem`デバッグコマンドでメモリの状態を監視したり、`var`文で変数の中身を書き換える事ができます。
デバッグを中断するには`exit`コマンドを用います。
## ライセンス
このSimpleプログラミング言語はMITライセンスの下で提供されています。詳細については、[LICENSE](LICENSE)ファイルを参照してください。

このプログラムはMITライセンスのもと、自由でオープンソースとして提供されており、誰もが利用、変更、および共有することができます。我々は子ども達の学びを支援し、プログラミング教育に貢献することを目指しています。
