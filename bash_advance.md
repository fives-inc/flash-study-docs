---
title: "Bash応用"
description: "Bash スクリプトの応用問題です"
date: 2023-06-28T01:00:00Z
image: /images/post/post-1.png
categories: ["bash"]
featured: true
syntax: false
draft: false
---

# question

引数としてディレクトリ名を受け取り、そのディレクトリ内のすべてのファイルの合計サイズを計算して出力するスクリプトを作成してください。

## answer

```bash
directory=$1
total_size=0

find "$directory" -type f -exec du -b {} + | awk '{total+=$1} END {print total}'
```

# question

引数としてディレクトリ名を受け取り、そのディレクトリ内のファイルのうち、最も新しいファイルの名前と最も古いファイルの名前を出力するスクリプトを作成してください。

## answer

```bash
directory=$1

newest_file=$(find "$directory" -type f -printf '%T@ %p\n' | sort -n | tail -n 1 | awk '{print $2}')
oldest_file=$(find "$directory" -type f -printf '%T@ %p\n' | sort -n | head -n 1 | awk '{print $2}')

echo "Newest file: $newest_file"
echo "Oldest file: $oldest_file"
```

# question

引数としてディレクトリ名を受け取り、そのディレクトリ内のファイルを拡張子ごとに分類して、各拡張子ごとにファイル数を出力するスクリプトを作成してください。

## answer

```bash
directory=$1

find "$directory" -type f | awk -F . '{print $NF}' | sort | uniq -c
```

# question

引数としてディレクトリ名と数値を受け取り、そのディレクトリ内のファイルのうち、指定されたサイズ以上のファイルの一覧を出力するスクリプトを作成してください。

## answer

```bash
directory=$1
size_threshold=$2

find "$directory" -type f -size +"$size_threshold"c
```

# question

引数としてディレクトリ名と拡張子を受け取り、そのディレクトリ内のファイルのうち、指定された拡張子に一致するファイルのサイズの総和を計算して出力するスクリプトを作成してください。

## answer

```bash
directory=$1
extension=$2
total_size=0

find "$directory" -type f -name "*.$extension" -exec du -b {} + | awk '{total+=$1} END {print total}'
```

# question

引数としてファイル名とキーワードを受け取り、そのファイル内の行のうち、指定されたキーワードに一致する行のみを抽出して出力するスクリプトを作成してください。

## answer

```bash
file=$1
keyword=$2

grep "$keyword" "$file"
```

# question

引数としてディレクトリ名、拡張子、アウトプットファイル名を受け取り、そのディレクトリ内のファイルのうち、指定された拡張子に一致するファイルの内容を結合して新しいファイルを作成してください。

## answer

```bash
directory=$1
extension=$2
output_file=$3

find "$directory" -type f -name "*.$extension" -exec cat {} + > "$output_file"
```

# question

引数としてディレクトリ名、拡張子、アウトプットファイル名を受け取り、そのディレクトリ内のファイルのうち、指定された拡張子に一致するファイルを圧縮して新しい圧縮ファイルを作成してください。

## answer

```bash
directory=$1
extension=$2
output_file=$3

find "$directory" -type f -name "*.$extension" -exec tar -czvf "$output_file" {} +
```

# question

引数としてディレクトリ名、拡張子、検索文字を受け取り、そのディレクトリ内のファイルのうち、指定された拡張子に一致するファイルの中で、特定の文字列を含むファイルを検索して出力するスクリプトを作成してください。

## answer

```bash
directory=$1
extension=$2
search_string=$3

grep -r -l "$search_string" "$directory"/*. "$directory"/*."$extension"
```

# question

引数としてディレクトリ名、拡張子、検索文字を受け取り、そのディレクトリ内のファイルのうち、指定された拡張子に一致するファイルの中で、指定された文字列を含む行のみを抽出して出力するスクリプトを作成してください。

## answer

```bash
directory=$1
extension=$2
search_string=$3

find "$directory" -type f -name "*.$extension" -exec grep "$search_string" {} +
```
