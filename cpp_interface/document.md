---
documentclass: ltjsarticle
---

\clearpage

# はじめに

この本でのインターフェスとは、ある共通の意味を持つクラスのメンバ関数であるとか、ある目的のために使用される特定のメンバ関数名であるとか、そう言ったものです。動的ポリモルフィズムのために継承して利用するインターフェースクラス、という狭い意味のインターフェースではありません。

JavaやC#などのインターフェースクラスを利用した動的ポリモルフィズムでは、インターフェース詳細はその基底となっているインターフェースクラスを見ればわかる場合が多いでしょう。
しかし、C++はそのようなインターフェースクラスによる制約を用いずテンプレートによるダックタイピングを多用します。この場合、あるテンプレートな処理において入力される型に必要なインターフェース、および同じ意味論を持つような複数の型に渡って統一されるインターフェースなどの把握は困難です。前者だけは、C++20で導入されるコンセプトによって制約および表示が可能になりますが、後者に関してはこれからもC++プログラマの暗黙的な合意の下で定義され続けます・・・。  
C++標準ライブラリだけを見ても、このような暗黙的に使用されているインターフェースがいくつもあります。本書ではこのことを「標準的インターフェース」と呼んでいます。また、標準ライブラリに新しいものが追加される際にもこれを意識した上でインターフェースが決定されています。

では、このような標準的インターフェースを知ると何が嬉しいのでしょう？知らなくてもプログラムはかけますが、知っておくと次のような利点があります。

1. 変更に強いプログラムを書くことができる
2. 標準もしくは外部ライブラリで用意されている機構に意識せずともアダプトできる
3. テンプレートな処理において受け入れ可能な型の門戸を広げられる
4. 関数の命名で悩まずにすみ、利用者にとっても自然な名前を選択できる

標準的インターフェースはある程度C++を書いていれば意識せずともなんとなく身についており、そうしたC++プログラマが書いたライブラリは自然と標準的インターフェースを意識したものになります。それを知っておけば、そのようなライブラリをあまり迷わずに使用でき、また、利用されやすいライブラリを書くことができるでしょう。そして、標準的インターフェースに基づいた世界でならばそれらライブラリの相互利用さえも自然に行うことができます。

本書は、この「なんとなく」な部分を明示的に探訪したものです。

ただし、何でもかんでもこの標準的インターフェースに合わせれば良いというものではありません。これもまた暗黙的な了解によるのですが、それぞれのインターフェースにはその意味論が確かに存在しています。あるインターフェースを選択した時は、その意味論に沿った処理を行い、期待される副作用をし、戻り値を返さなければなりません。これは、よく演算子オーバーロードで例に挙げられる、「`operator+()`を不適切にオーバーロードすれば`a + b`で引き算を行うことができる（もちろん、やらないことが推奨される）」というお話に通じるものがあります。

本書では、このようなインターフェースの意味論についても説明をしてあるつもりです。これらのことを知っておけば、C++に対する理解を一段と深めることが出来、より良いプログラムを書くことができるようになるでしょう。

\clearpage

# イテレータインターフェース

C++STLの基本理念の柱でもあり、おそらく最も基本的で自然に出会うのがこのイテレータインターフェースではないかと思います。

## イテレート可能な型のインターフェース

イテレート可能な型というのは例えば、`std::vector`のようなイテレータによってその要素を列挙することのできる型のことです。STLでは、イテレータを介すことでコンテナとアルゴリズムをお互いの実装詳細から分離し、なおかつコンテナからイテレータを引き出す操作は共通化されているため、あるアルゴリズムを使用する際にコンテナの詳細をほとんど意識する必要がなくなるようになっています。

### `begin(), end()`

#### `cbegin(), cend()`

#### アダプトする場合

### リバースイテレータ

### イテレータ特性

## イテレータ型のインターフェース

イテレータ型というのは、イテレータそのものの型のことです。せっかくイテレータという概念でアルゴリズムとコンテナを分離しているのに、イテレータ型によって操作が異なってしまうと抽象化の意味がありません。そのため、C++で利用されるイテレータのインターフェースは統一されています。

### forward iterator

#### `operator++()`

#### `operator*()`

#### `operator!=()`

### bidirectional iterator

### random access iterator

### 全イテレータ共通の型インターフェース

# コンテナインターフェース

# タプルインターフェース

# 文字列インターフェース

# 関数呼び出しインターフェース

# アロケーターインターフェース

# `swap`インターフェース

# メタ関数のインターフェース