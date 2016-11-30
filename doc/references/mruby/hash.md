# Hashクラス

ハッシュテーブルを扱うクラスについて紹介します。  
ハッシュテーブルは、キーと値を関連付けたデータの集合です。  

```ruby
hash_table = {:key => "値"}
speak(hash_table[:key]) # 「値」と表示される
```

## ハッシュテーブルの生成

```ruby
hash_table = {:name => "rmake", :hp => 150}
```

## 値の取得

```ruby
hash_table = {:name => "rmake", :hp => 150}
name = hash_table[:name]
hp = hash_table[:hp]
```

## 値の挿入

```ruby
hash_table = {}
hash_table[:name] = "CoR" # {:name => "CoR"}
```

## 値の代入

```ruby
hash_table = {:name => "rmake", :hp => 150}
hash_table[:name] = "Code on Rmake" # {:name => "Code on Rmake", :hp => 150}
```

## deleteメソッド

キーに関連する値を削除します。

```ruby
hash_table = {:name => "rmake", :hp => 150}
hash_table.delete(:hp)
```

* 第1引数：キー

## eachメソッド

全要素を探索するループを書くことができます。

```ruby
hash_table = {:name => "rmake", :hp => 150}
hash_table.each do |key, value|
  speak("全要素を探索するループ: #{key}, #{value}")
end
```

## keysメソッド

キーの一覧を配列で返します。  

```ruby
hash_table = {:name => "rmake", :hp => 150}
keys = table.keys
```

## valuesメソッド

値の一覧を配列で返します。

```ruby
hash_table = {:name => "rmake", :hp => 150}
values = hash_table.values
```

