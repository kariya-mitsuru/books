---
title: C++20 Modules
author: onihusube
date: 2020/01/05
geometry:
  width: 154cm
  height: 216cm
  margin: 1in
okuduke:
  revision: 初版
  printing: ねこのしっぽ
---
\clearpage

# はじめに

## モジュールとは？

## 本書の内容について

本書ではC++20のモジュール仕様について、規格書の文面から読み取ることのできる理論的な部分を解説しています。従って、規格書では触れられていないビルドについてや`.dll, .lib, .so, .a`などの特殊な翻訳単位については触れていません。

なお、本書執筆時点では完全にモジュールを実装した処理系は存在していないため、本書の内容は実装に裏打ちされたものではなく、あくまで規格書から読み取った理論的なものにとどまります。その解釈にはおそらくいくつか間違いがあるかと思われます、ご了承ください。

また、紙面の都合から翻訳単位、ヘッダファイルと`#include`、分割コンパイル、翻訳単位越え、リンケージ、テンプレートのインスタンス化、名前探索等、知っておいた方が良いと思われる知識については解説していません。分からない単語や概念に出くわしたら適宜調べてみることをお勧めします。

\clearpage

# 言葉の事前定義

モジュールの説明ではどうしてもいくつか特有の言葉を導入しなければならず、しかもそれが前後しがちなので、事前に簡単かつ順番に言葉を定義しておきます。

一部の言葉は後で詳細に説明されます。

### モジュール宣言（*module decralation*）

ある翻訳単位をモジュールを記述するものとして表明する宣言文。`export module modulename;`もしくは`module modulename;`のような宣言。

### モジュール単位（*module unit*）

モジュール宣言を含む翻訳単位。

### モジュール名（*module name*）

モジュール宣言において指定した名前。1つの名前を複数のモジュール単位で共有できる。

### ヘッダーユニット（*header unit*）

従来のヘッダファイルを仮想的にモジュール単位として扱う仕組み、もしくはその場合のモジュール単位のこと。指定されたヘッダファイル1つで1つの翻訳単位をなす。

### 名前付きモジュール（*named module*）

同じモジュール名を持つモジュール単位の集合。名前付きモジュールが1つのモジュールとなる。

ヘッダーユニットは名前付きモジュールではない（モジュール宣言によってモジュールとなるわけではないため）。

### エンティティ

クラス、関数、変数など、C++コード上で名前を持つことができ、何かしらの意味論を持つものの総称。本書では主に、名前空間スコープに宣言できるものを対象にしている。

### エクスポート（`export`）

あるモジュールのエンティティを、そのモジュール外部から使用できるようにするために、`export`を付加した宣言を行うこと。

### モジュールのインターフェース

ある名前付きモジュールにおいて、モジュール宣言に`export`を含むモジュール単位の集合、もしくはそこでエクスポートされている宣言の集合。

### グローバルモジュールフラグメント

あるモジュール単位において、モジュール宣言より前に`module;`というマーカーを置いた時、そこからモジュール宣言の直前までの領域の事。そこはモジュールには含まれない。

グローバルモジュールフラグメントには直接的にはプリプロセッサディレクティブしか現れてはならない。

### グローバルモジュール

グローバルモジュールフラグメントと全てのモジュール単位ではない翻訳単位の集合。

### モジュール単位の本文（*module unit purview*）

モジュール宣言から始まりその翻訳単位の終わり（実質的にそのファイル末尾）までの部分に書かれている文字列。名前付きモジュールの本文とは、名前付きモジュールを構成する個々のモジュールの本文の集合。

モジュール宣言から始まるため、グローバルモジュールフラグメントはモジュールの本文には含まれない。

グローバルモジュールの本文とは、グローバルモジュールに現れている宣言全てのこと（グローバルモジュールフラグメントも含む）。

### モジュールに属する（*attached*）

名前付きモジュールの本文内に書かれた宣言は全て、そのモジュールに属している。

そうでないもの（グローバルモジュールフラグメント内宣言等）は、グローバルモジュールに属している。


### 可視と到達可能

### `import`

### 再エクスポート




\clearpage

# モジュールの基本

## モジュールのインターフェース

## モジュールの実装

# 可視・到達可能・ODR

# `export`

# `import`

# 変なモジュール

## グローバルモジュール

### グローバルモジュールフラグメント

## ヘッダーユニット

### `#include`からの置換

## プライベートモジュールフラグメント（単一ファイルのモジュール）

# モジュールと`inline`宣言

# モジュールとテンプレート

## ADL