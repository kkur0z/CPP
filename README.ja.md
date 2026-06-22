# CPP

English: [README.md](README.md)

このリポジトリは、42 C++ Piscine のモジュール `00` から `09` までをまとめたトップレベルリポジトリです。各モジュールは Git submodule として管理されており、それぞれに複数の C++98 演習、README、Makefile、ソースファイル、ヘッダーがあります。

演習は、基本的な C++ 構文とクラスから始まり、継承、ポリモーフィズム、例外、テンプレート、STL コンテナ、パース、ソートまで段階的に扱います。

## モジュール

| Module | 内容 | README |
| --- | --- | --- |
| `00` | 基本文法、標準入出力、クラス、static member | [00/README.md](00/README.md) |
| `01` | メモリ確保、参照、ポインタ、ファイル I/O | [01/README.md](01/README.md) |
| `02` | Orthodox Canonical Form、固定小数点数、演算子オーバーロード | [02/README.md](02/README.md) |
| `03` | 継承、多重継承 | [03/README.md](03/README.md) |
| `04` | ポリモーフィズム、抽象クラス、deep copy、interface | [04/README.md](04/README.md) |
| `05` | 例外、バリデーション、Form、factory | [05/README.md](05/README.md) |
| `06` | C++ cast、scalar conversion、serialization、実行時型識別 | [06/README.md](06/README.md) |
| `07` | 関数テンプレート、反復用テンプレート、テンプレート配列 | [07/README.md](07/README.md) |
| `08` | テンプレートコンテナ、iterator、algorithm、stack adaptation | [08/README.md](08/README.md) |
| `09` | STL コンテナ、ファイルパース、RPN 評価、merge-insertion sort | [09/README.md](09/README.md) |

## 前提条件

- `c++` として使える C++ コンパイラ
- `make`
- submodule を扱える `git`
- Unix 系 shell

各演習の Makefile は次の設定でコンパイルします。

```sh
c++ -Wall -Wextra -Werror -pedantic -std=c++98
```

## インストール

submodule を含めてリポジトリを clone します。

```sh
git clone --recurse-submodules <repository-url>
cd CPP
```

すでに submodule なしで clone している場合は、次のコマンドで初期化します。

```sh
git submodule update --init --recursive
```

submodule の remote は [.gitmodules](.gitmodules) に記載されています。

## ビルド

トップレベルの Makefile はありません。リポジトリルートから `make -C` で各演習をビルドします。

```sh
make -C 00/ex00
make -C 01/ex04
make -C 09/ex02
```

各演習の Makefile は通常の target を持っています。

```sh
make
make clean
make fclean
make re
```

これらは演習ディレクトリ内で実行するか、`make -C` で対象ディレクトリを指定して実行します。

## 使い方

各演習はそれぞれの実行ファイルを生成します。正確なコマンドや引数は各モジュールの README を参照してください。例:

```sh
./00/ex00/megaphone "hello world"
```

```sh
cd 01/ex04
./file_replace filename s1 s2
```

```sh
cd 09/ex01
./RPN "8 9 * 9 - 9 - 9 - 4 - 1 +"
```

ローカルファイルを読み込んだり出力ファイルを作成したりするため、演習ディレクトリから実行することを前提にしているものもあります。

## テスト

リポジトリ全体の test runner はありません。各演習の `main.cpp` と Makefile を使って確認します。

```sh
make -C 00/ex00 re
make -C 06/ex00 re
make -C 09/ex02 re
```

## プロジェクト構成

```text
.
├── 00/ ... 09/      # Git submodule として管理される C++ Piscine modules
├── .gitmodules      # submodule の path と remote URL
├── README.md        # 英語のトップレベルガイド
└── README.ja.md     # 日本語のトップレベルガイド
```

各モジュール内では、演習は `ex00`、`ex01` のように分かれています。多くの演習には `Makefile`、`src/` の実装ファイル、`include/` のヘッダーがあります。

## メモ

- この root repository は 10 個の module repository への索引です。
- ビルドや実行の詳細は各 module README にあります。
- 生成された object file や実行ファイルは、対応する演習ディレクトリで `make clean` または `make fclean` を実行すると削除できます。
