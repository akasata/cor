# Arrayクラス

配列を扱うクラスについて紹介します。

## 配列の生成

```ruby
arr = [1, 2, 3]
```

## to_sメソッド

配列を文字列に変換します。

```ruby
str = [1, 2, 3].to_s
```

## 要素にアクセスする

```ruby
arr = [15, 32, 13]
num = arr[2] # 13
```

## popメソッド

最後尾の要素を抜き出して、配列からは削除します。

```ruby
arr = [1, 2, 3]
last_value = arr.pop # last_value: 3, arr: [1, 2]
```

## pushメソッド

配列に要素を追加します。

```ruby
arr = [1, 2, 3]
arr.push(4) # [1, 2, 3, 4]
```

以下のような書き方もできます。 

```ruby
arr = [1, 2, 3]
arr << 5 # [1, 2, 3, 5]
```

## include?メソッド

指定した値が配列に含まれているかどうかチェックします。

```ruby
arr = [1, 2, 3]
result = arr.include?(1) # true
```

* 第1引数：指定した値

## 配列が等しいかどうか

配列が等しいかどうかチェックします。

```ruby
arr1 = [1, 2, 3]
arr2 = [1, 2, 3]

result = arr1 == arr2 # true
```

## eachメソッド

配列の要素を探索するループを記述することができます。

```ruby
arr = [1, 2, 3]
arr.each do |item|
  # 3回実行され、itemに配列の要素が格納される（1, 2, 3と順番に変わる）
  speak("ループ(each): #{item}")
end
```

## mapメソッド

戻り値を集めた配列を作成できます。

```ruby
arr = [1, 2, 3]
generated_arr = arr.map do |item|
  item * 2
end

# generated_arr: [2, 4, 6]
```

## findメソッド

配列に含まれている要素を探索するメソッドです。  
最初に見つかった要素を返します。 

```ruby
arr = [1, 5, 3, 2 ,3]
result = arr.find do |item|
  item == 2
end

# result: 2
```

## find_allメソッド

配列に含まれている要素を全て探索するメソッドです。  
配列が返ります。 

```ruby
arr = [1, 2, 3, 4, 5, 6, 7, 8]
result = arr.find_all do |item|
  # 2で割り切れる
  item % 2 == 0
end

# result: [2, 4, 6, 8]
```

## sortメソッド

配列を並び替えるメソッドです。

```ruby
arr = [3, 4, 1, 2]
sorted_arr = arr.sort # [1, 2, 3, 4]
```

以下のような書き方で逆順にもできます。 

```ruby
arr = [3, 4, 1, 2, 5]
sorted_arr = arr.sort do |a, b|
  b <=> a
end

# sorted_arr: [5, 4, 3, 2, 1]
```


