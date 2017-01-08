# 基本メソッド

## debug_log

ログエリアにデバッグログを出力するメソッドです。

```ruby
debug_log 'こんにちは、Rmake！'
```

* 第一引数：出力ログのテキスト

## require_code

シーンに含まれるソースファイルを読み込みます。

```ruby
require_code 'defines.rb'
```

* 第一引数：ソースファイル名

## シーンの開始：start_scene

シーンを開始するメソッドです。

```ruby
start_scene "start"
```

* 第一引数：開始するシーン名

## ゲームクリア：game_clear

ゲームクリアして、ゲームクリア画面に移行します。

```ruby
game_clear
```
