# テキストスプライト

## シーンのcreate/updateブロックにおけるput_textメソッド

テキストスプライト定義で定義したテキストスプライトを配置することができます。  

* 第一引数：スプライトテキスト定義名
* 戻り値：スプライト

```ruby
text_sprite = put_text 'basic-text' do
  position 400, 50
  text 'こんにちは、Rmake'
end
```

## textメソッド

テキストスプライトに表示する文章を変更/取得するメソッドです。  

```ruby
# テキストを設定する
text_sprite.text 'Hello!'

# テキストを取得する
my_text = text_sprite.text
```

* 第一引数：表示するテキスト
