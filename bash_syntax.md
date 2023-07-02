---
title: "Bash基本文法"
description: "Bash スクリプトの基本文法です"
date: 2023-05-13T01:00:00Z
image: /images/post/post-1.png
categories: ["bash"]
featured: true
syntax: true
draft: false
---

Bash（Bourne Again SHell）は、Linux システムで一般的に使用されるシェルスクリプト言語です。以下に、Bash の基本的な文法要素を説明します。

- コメント: `#` を使用してコメントを追加できます。 `#` 以降のテキストは無視されます。

```bash
# これはコメントです
```

- 出力: `echo` コマンドを使用してテキストを出力できます。
- エスケープ: 特殊文字をエスケープするために、バックスラッシュ `\` を使用します。

```bash
echo "Hello, World!"
echo "This is a \"quoted\" text."
```

- 変数: 変数を宣言し、値を割り当てることができます。変数名は英数字とアンダースコアで構成され、先頭は文字で始める必要があります。
- 変数の展開: 変数を参照する場合、`$` を使って変数名を展開します。

```bash
name="John"
age=25

echo "Hello, $name!"
```

- 条件分岐: `if` 文を使用して条件分岐を行います。
  - 条件分岐の追加オプション: `elif` を使用して、複数の条件をチェックします。

```bash
if [ condition ]; then
  # 条件が真の場合に実行されるコマンド
else
  # 条件が偽の場合に実行されるコマンド
fi
```

- case 文: 複数のパターンに基づいて分岐するための `case` 文を使用します。

```bash
case 値 in
  パターン1)
    # パターン1に該当したときに実行されるコマンド
    ;;
  パターン2)
    # パターン2に該当したときに実行されるコマンド
    ;;
  ...
  パターンn)
    # パターンnに該当したときに実行されるコマンド
    ;;
esac
```

- ループ: `for` ループや `while` ループを使用して反復処理を行います。

```bash
for variable in list; do
  # 反復処理のコマンド
done

while condition; do
  # 条件が真の間、反復処理のコマンド
done
```

- 条件式: `test` コマンドまたは `[[...]]` 構文を使用して条件式を評価します。
  - 条件式の拡張: `[[ ... ]]` 構文を使用すると、より高度な条件式を作成することができます。例えば、文字列の比較やパターンマッチングが可能です。

```bash
# test コマンドを使用した条件式
if test $x -eq 5; then
  echo "x is equal to 5"
fi

# [[]] 構文を使用した条件式
if [[$x -eq 5]]; then
  echo "x is equal to 5"
fi
```

- 関数: 関数を定義して再利用可能なコードブロックを作成できます。

```bash
function my_function() {
  # 関数のコマンド
}

# 関数を呼び出す
my_function
```

- コマンド置換: コマンドの実行結果を変数に割り当てるために、バッククオート \` もしくは `$()` を使用します。

```bash
files=`ls`
count=$(wc -l file.txt)
```

- 配列: 配列を宣言し、要素にアクセスすることができます。
  - 配列の要素数を取得するには、 `${#array[@]}` を使用します。
  - 配列の要素をスライスするには、 `${array[@]:start:length}` を使用します。

```bash
my_array=("apple" "banana" "orange")
echo ${my_array[1]}  # "banana"
```

- リダイレクション: 標準入力や標準出力のリダイレクションを行うことができます。

```bash
command > output.txt # 標準出力をファイルにリダイレクト
command < input.txt # ファイルから標準入力にリダイレクト
```

- パイプ: パイプ `|` を使用して、コマンドの出力を別のコマンドの入力としてつなげることができます。

```bash
command1 | command2 # command1 の出力を command2 の入力として渡す
```

- リダイレクションの追加オプション:

  - `>>` : ファイルに追記するためのリダイレクト。既存の内容の後ろに出力を追加します。
  - `2>` : 標準エラー出力をファイルにリダイレクトします。
  - `2>>` : 標準エラー出力をファイルに追記します。
  - `&>` : 標準エラーと標準出力を同じファイルにリダイレクトします

- ヒアドキュメント: `<<` を使用して、インラインで複数行のテキストを指定します。

- コマンドの終了ステータスの確認: 直前に実行したコマンドの終了ステータスを確認するためには、`$?` 変数を使用します。

```bash
command
status=$?
echo "Exit status: $status"
```

- 文字列の操作:

  - 変数の値を連結するには、`${var1}${var2}` のように連結します。
  - 文字列の長さを取得するには、 `${#var}` を使用します。

- 数値演算:

  - 数値の計算には、`expr` コマンドや `$(( ... ))` 構文を使用します。
  - 数値の比較には、`-eq` （等しい）、 `-ne` （等しくない）、 `-lt` （より小さい）、 `-gt` （より大きい）などの比較演算子を使用します。

- プロセス制御:
  - バックグラウンド実行: コマンドの末尾に `&` を付けると、そのコマンドをバックグラウンドで実行します。
  - ジョブ制御: `fg` および `bg` コマンドを使用して、バックグラウンドジョブをフォアグラウンドまたはバックグラウンドに移動します。