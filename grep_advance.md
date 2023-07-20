---
title: "grep応用"
description: "grep の応用問題です"
date: 2023-07-06T01:00:00Z
image: /images/post/grep-advance.png
categories: ["grep"]
featured: false
syntax: false
draft: false
---

grep の基本文法を使って応用問題をやっていきましょう！

まずは List を見ながら問題を解いていき、ある程度覚えたら Flash Card にチャレンジしてください！

各問には制限時間があり、時間内に答えを出してください。エディタを用意して実際に書いてみると記憶に残りやすいのでおすすめです！

# question

ファイル emails.txt から.com ドメインのメールアドレスのみを抽出して表示するコマンドを書いてください。

## answer

```bash
grep -E '\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}\b' emails.txt | grep '\.com$'
```

# question

ファイル words.txt から 3 文字の単語のみを表示するコマンドを書いてください。

## answer

```bash
grep -E '\b[A-Za-z]{3}\b' words.txt
```

# question

ファイル data.txt から行の先頭が数字の行のみを表示するコマンドを書いてください。

## answer

```bash
grep '^[0-9]' data.txt
```

# question

ファイル data.txt から空行を含む連続した行のブロック（1 つ以上の連続した空行から成る）を表示するコマンドを書いてください。

## answer

```bash
grep -Ez '\n\n+' data.txt
```

# question

ファイル data.txt から日付が `2023-07-16` の形式に一致する行のみを表示するコマンドを書いてください。

## answer

```bash
grep -E '2023-07-16' data.txt
```

# question

ファイル data.txt から apple または orange が含まれない行のみを表示するコマンドを書いてください。

## answer

```bash
grep -v -E 'apple|orange' data.txt
```

# question

ファイル data.txt から行の長さが 20 文字以上の行のみを表示するコマンドを書いてください。

## answer

```bash
grep -E '.{20,}' data.txt
```

# question

ディレクトリ files 内のファイルから文字列 search を含み、かつ行番号が 10 行目以上の行のみを表示するコマンドを書いてください。

## answer

```bash
grep -n -r -E 'search' files/ | awk -F':' '$1 > 9 {print}'
```

# question

ディレクトリ logs 内のファイルのうち、文字列 ERROR が含まれる行の前後 3 行を含むブロックを表示するコマンドを書いてください。

## answer

```bash
grep -B 3 -A 3 -r 'ERROR' logs/
```

# question

ディレクトリ files 内のすべてのファイルから文字列 search を含む行を表示し、各行のファイル名も表示するコマンドを書いてください。

## answer

```bash
grep -r -H 'search' files/
```

# question

ディレクトリ logs 内のファイルから ERROR と WARNING が同じ行に含まれる行のみを表示するコマンドを書いてください。

## answer

```bash
grep -E 'ERROR.*WARNING|WARNING.*ERROR' logs/\*
```

# question

ディレクトリ data 内のファイルのうち、文字列 apple が 3 回以上出現する行のみを表示するコマンドを書いてください。

## answer

```bash
grep -E '(apple._){3,}' data/_
```

# question

ディレクトリ files 内のファイルのうち、文字列 search を含む行を表示し、行番号も表示するコマンドを書いてください。ただし、行番号はファイルごとにリセットされるようにしてください。

## answer

```bash
grep -Hn 'search' files/\*
```

# question

ファイル data.txt の中で apple と orange が両方とも含まれる行を表示するコマンドを書いてください。

## answer

```bash
grep -E 'apple.*orange|orange.*apple' data.txt
```

# question

ディレクトリ logs 内のファイルから文字列 ERROR を含む行を表示し、ファイルごとに ERROR の出現回数も表示するコマンドを書いてください。

## answer

```bash
grep -r 'ERROR' logs/ | awk -F':' '{print $1, $2}' | sort | uniq -c
```
