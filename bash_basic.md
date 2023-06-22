---
title: "Bash基礎"
description: "Bash スクリプトの基本問題です"
date: 2023-05-14T01:00:00Z
image: /images/post/post-1.png
categories: ["bash"]
featured: false
draft: false
---

# question

`echo "Hello, World!"` というコマンドを実行したときの出力は何ですか？

## answer

"Hello, World!"

# question

for ループを使用して、1 から 10 までの数字を出力するスクリプトを書いてください。

## answer

```bash
for i in {1..10} ; do
    echo $i
done
```

# question

ユーザーにパスワードを入力させ、そのパスワードが「password」と一致するかどうかを検証するスクリプトを書いてください。

## answer

```bash
read -s -p "Enter Password: " password
if [ $password = "password" ]
then
  echo "Access granted"
else
  echo "Access denied"
fi
```

# question

引数として 2 つの数字を受け取り、それらを掛け合わせた結果を出力するスクリプトを書いてください。

## answer

```bash
product=$(($1 * $2))
echo "Product of $1 and $2 is $product"
```

# question

引数としてディレクトリ名を受け取り、そのディレクトリ内のファイルの一覧を出力するスクリプトを書いてください。

## answer

```bash
dir=$1
for file in $dir/*
do
  echo $file
done
```

# question

引数として文字列を受け取り、その文字列をすべて大文字に変換した結果を出力するスクリプトを書いてください。

## answer

```bash
string=$1
upper=$(echo $string | tr '[:lower:]' '[:upper:]')
echo $upper
```

# question

ファイル file.txt に、1 から 10 までの数字を 1 行に 1 つずつ書いたものがあります。そのファイルから数字を読み取り、それらの合計を出力するスクリプトを書いてください。

## answer

```bash
sum=0
while read num
do
  sum=$((sum + num))
done < file.txt
echo "Sum is $sum"
```

# question

引数としてファイル名を受け取り、そのファイルの行数を出力するスクリプトを書いてください。

## answer

```bash
file=$1
lines=$(wc -l < $file)
echo "Number of lines in $file is $lines"
```

# question

引数としてファイル名を受け取り、そのファイル内で最も長い行の文字数を出力するスクリプトを書いてください。

## answer

```bash
file=$1
longest=$(wc -L < $file)
echo "Length of longest line in $file is $longest"

# L オプションがない場合
file="$1"
max_length=0

while IFS= read -r line; do
  length=${#line}
  if (( length > max_length )); then
    max_length=$length
  fi
done < "$file"

echo "最も長い行の文字数: $max_length"
```

# question

引数としてファイル名を受け取り、そのファイル内で最も頻繁に出現する単語を出力するスクリプトを書いてください。ただし、スペースで区切られた単語のみをカウントし、単語の出現頻度が同じ場合は、最初に出現した単語を優先します。

## answer

```bash
file=$1
awk '{for(i=1;i<=NF;i++){print $i}}' $file | sort | uniq -c | sort -nr | awk '{print $2; exit}'
```
