---

### ”Learn You a Haskell  for Great Good!”を読んでみた
<br>
日本女子大学大学院
<br>
数理・物性構造科学専攻
<br>
理学研究科 1年
<br>
松本彩花

---
### An intro to lists
- ハスケルでは、リストは同種のデータ構造
  - 同じ型のいくつかの要素が保存できる

  
---
### リストの定義
```
ghci> let lostNumbers = [4,8,15,16,23,42]  
ghci> lostNumbers  
[4,8,15,16,23,42]  
```
- GHCIでは名前を定義するために、letを使う
  - (例)let a=1とa=1はGHCI上で同じ意味
- 文字列はリストなので、リスト関数を使用することが出来る
 - "hello"は['h'、 'e'、 'l'、 'l'、 'o']を省略した糖衣構文のリスト


---
### リストの連結1

- リスト同士は++で繋げることが出来る
```
ghci> [1,2,3,4] ++ [9,10,11,12]  
[1,2,3,4,9,10,11,12]  
ghci> "hello" ++ " " ++ "world"  
"hello world"  
ghci> ['w','o'] ++ ['o','t']  
"woot"  
```
---
### リストの連結２

- : で文字列同士または数字とリストを繋げることが出来る
  - (例)[1,2,3]は1:2:3:[]の糖衣構文
  
```
ghci> 'A':" SMALL CAT"  
"A SMALL CAT"  
ghci> 5:[1,2,3,4,5]  
[5,1,2,3,4,5]  
```

  - Note: []はからのリスト、[[]]はからのリストを一つ含んだリスト、[[],[],[]]はからのリストを3つ含んだリスト

---
### リストからの抽出

- !! <数字>でリストの中から0から数えて<数字>番目の要素を取り出す

```
ghci> "Steve Buscemi" !! 6  
'B'  
ghci> [9.4,33.2,96.2,11.2,23.25] !! 1  
33.2 
```
- 4つの要素しかないリストで、6つの要素を取り出そうとするとエラーになる

---
### Listの入れ子

- リストの中に、リストを含むことが出来る
- [1,1,a,2]が作れないように、[[1,1,1],[a,a,a]]も作れない

```
ghci> let b = [[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3]]  
ghci> b  
[[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3]]  
ghci> b ++ [[1,1,1,1]]  
[[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3],[1,1,1,1]]  
ghci> [6,6,6]:b  
[[6,6,6],[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3]]  
ghci> b !! 2  
[1,2,2,3,4] 
```

---
### リストの比較

- リストの要素を比較することによって、リストを比較する
- それぞれのリストの先頭要素から順に要素が比較される

```
ghci> [3,2,1] > [2,1,0]  
True  
ghci> [3,2,1] > [2,10,100]  
True  
ghci> [3,4,2] > [3,4]  
True  
ghci> [3,4,2] > [2,4]  
True  
ghci> [3,4,2] == [3,4,2]  
True  
```

---
<span style="color: red; "> head</span>:リストの先頭要素を取得

```
ghci> head [5,4,3,2,1]  
5   
```
<br>

 <span style="color: red; "> tail </span>:リストの先頭要素を取り除く

```
ghci> tail [5,4,3,2,1]  
[4,3,2,1]   
```
<br>

 <span style="color: red; "> last</span>:リストの最後の要素を返す

```
ghci> last [5,4,3,2,1]  
1   
```

---
 <span style="color: red; "> init</span>:最後の要素以外の全てを返す

```
ghci> init [5,4,3,2,1]  
[5,4,3,2] 

```
<br>

空のリストでは、エラーが出る
からのリストでは、head,tail,init,lastは使えない

```
ghci> head []  
*** Exception: Prelude.head: empty list 

```

---
 <span style="color: red; "> length </span>
 
 length [リスト]:リストの長さを返す

```
ghci> length [5,4,3,2,1]  
5  

```

 <span style="color: red; "> null</span> 
 
 null [リスト]:リストが空か確認する


```
ghci> null [1,2,3]  
False  
ghci> null []  
True 
ghci> let xs=[1,2,3]
ghci> null xs
False
ghci> let xs =[]
ghci> null xs
True
```

<span style="color: red; "> reverse </span>
reverse [リスト]:リストの要素を逆順にする

```
ghci> reverse [5,4,3,2,1]  
[1,2,3,4,5]  

```

---
 <span style="color: red; ">take </span>
 <br>
take <数字> [リスト]:リストの初めの要素から<数字>番目の要素まで取り出す。

リストよりも長い要素数を取り出そうとすると、そのままのリストが返る
<数字>を0にすると、空のリストが返る

```
ghci> take 3 [5,4,3,2,1]  
[5,4,3]  
ghci> take 1 [3,9,3]  
[3]  
ghci> take 5 [1,2]  
[1,2]  
ghci> take 0 [6,6,6]  
[]  
```

---
 <span style="color: red; ">drop </span>
drop <数字> [リスト]:

---
### Texas ranges

1から20の要素が入ったリストは、
[1..20]
のように省略して表すことが出来る
aからzも同様に表せる
```
ghci>[1..20]
[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]
ghci>['a'..'z']
"abcdefghijklmnopqrstuvwxyz"
ghci>['K'..'Z']
"KLMNOPQRSTUVWXYZ"

```
---
### 倍数のリスト

2,4..20のような倍数の要素の場合は、はじめの２つの要素を,で区切ってから、要素の最大値を指定する

```
ghci>[2,4..20]
[2,4,6,8,10,12,14,16,18,20]
ghci>[3,6..20]
[3,6,9,12,15,18]
```

---
<span style="color: red; "> cycle</span> 無限のリストの中で、リストと周期をとる
take <数字> (cycle[要素])
リストの中身の要素を周期的に<数字>個まで繰り返す

```
ghci>take 10 (cycle[1,2,3])
[1,2,3,1,2,3,1,2,3,1]
ghci>take 12 (cycle"LOL ")
"LOL LOL LOL "
```

---
 <span style="color: red; ">repeat</span>

要素をとり、その要素の無限のリストを生成する
一つの要素のみを用いた周期的なリストのようである
 take <数字1> (repeat <数字2>)
<数字1>回分<数字2>を繰り返し表示する

```
ghci>take 10 (repeat 5)
[5,5,5,5,5,5,5,5,5,5]
```

---
<span style="color: red; "> replicate </span>

リストの中で同じ要素のいくつかの数が欲しい場合

```
replicate <数字1> <数字2> 
<数字1>この<数字2>を出力する
```





