---
title: "grep基礎"
description: "grep の基礎問題です"
date: 2023-07-05T01:00:00Z
image: /images/post/grep-basic.png
categories: ["grep"]
featured: false
syntax: false
draft: false
---

grep の基本文法を使って基礎問題をやっていきましょう！

まずは List を見ながら問題を解いていき、ある程度覚えたら Flash Card にチャレンジしてください！

各問には制限時間があり、時間内に答えを出してください。エディタを用意して実際に書いてみると記憶に残りやすいのでおすすめです！

問題文中の data.txt は以下として考えてください

```
apple
banana

orange
pineapple

apple banana
orange pineapple
apple orange

banana pineapple
orange apple
```

# question

ファイル data.txt から文字列 apple を含む行をすべて表示するコマンドを書いてください。

## answer

```bash
grep "apple" data.txt
```

# question

ファイル data.txt から文字列 banana を含む行を除外して表示するコマンドを書いてください。

## answer

```bash
grep -v "banana" data.txt
```

# question

ファイル data.txt から文字列 orange が含まれる行の行数を表示するコマンドを書いてください。

## answer

```bash
grep -c "orange" data.txt
```

# question

ファイル data.txt から大文字と小文字を区別せずに文字列 Pineapple が含まれる行を表示するコマンドを書いてください。

## answer

```bash
grep -i "Pineapple" data.txt
```

# question

ファイル data.txt の中で apple または orange を含む行を表示するコマンドを書いてください。

## answer

```bash
grep "apple\|orange" data.txt
```

# question

ファイル data.txt の中で apple と orange を含む行を表示するコマンドを書いてください。

## answer

```bash
grep "apple.*orange\|orange.*apple" data.txt
```

# question

ファイル data.txt から行番号を含めて文字列 banana を含む行を表示するコマンドを書いてください。

## answer

```bash
grep -n "banana" data.txt
```

# question

ファイル data.txt の中で単語として apple を含む行を表示するコマンドを書いてください。

## answer

```bash
grep -w "apple" data.txt
```

# question

ファイル data.txt から空行を含む行を表示するコマンドを書いてください。

## answer

```bash
grep "^$" data.txt
```

# question

ディレクトリ documents 内のすべてのファイルから文字列 important を含む行を表示するコマンドを書いてください。

## answer

```bash
grep "important" documents/\*
```

# question

ディレクトリ documents 内のすべてのファイルから文字列 TODO を含む行を表示し、行番号も表示するコマンドを書いてください。

## answer

```bash
grep -n "TODO" documents/\*
```

# question

ディレクトリ logs 内のファイルのうち、拡張子が `.log` であり、文字列 ERROR を含む行を表示するコマンドを書いてください。

## answer

```bash
grep "ERROR" logs/\*.log
```

# question

ディレクトリ documents 内のファイルのうち、文字列 apple を含む行を表示し、その行の前後 5 行も一緒に表示するコマンドを書いてください。

## answer

```bash
grep -C 5 "apple" documents/\*
```

# question

ディレクトリ data 内のファイルのうち、文字列 apple を含まない行を表示するコマンドを書いてください。

## answer

```bash
grep -v "apple" data/\*
```

# question

ディレクトリ documents 内のファイルから文字列 important を含む行のみを抽出し、新しいファイル important.txt に保存するコマンドを書いてください。

## answer

```bash
grep "important" documents/\* > important.txt
```
