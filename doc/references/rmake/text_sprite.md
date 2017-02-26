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

## colorメソッド

テキストスプライトに表示する文章の色を変更/取得するメソッドです。  

```ruby
# テキストの色を赤(#FF0000)にする
text_sprite.color '#FF0000'

# テキストの色を取得する
my_color = text_sprite.color
```

* 第一引数：文字の色

## font_sizeメソッド

テキストスプライトに表示する文字の大きさ（高さ）を変更/取得するメソッドです。  

```ruby
# 文字の大きさを18pxにする
text_sprite.font_size 18

# 文字の大きさを取得する
my_font_size = text_sprite.font_size
```

* 第一引数：フォントの大きさ（高さ、ピクセル数）

## boldメソッドメソッド

テキストスプライトに表示する文字を太文字にするかどうか設定/取得するメソッドです。

```ruby
# テキストを太文字にする
text_sprite.bold true

# 太文字かどうか取得する
my_bold = text_sprite.bold
```

* 第一引数：太文字にするかどうか（true/false）

## italicメソッド

テキストスプライトに表示する文字を斜体（イタリック）にするかどうか設定/取得するメソッドです。

```ruby
# テキストを斜体にする
text_sprite.italic true

# 斜体かどうか取得する
my_italic = text_sprite.italic
```

* 第一引数：斜体にするかどうか（true/false）

## wordwrapメソッド

テキストプライトに表示する文章を折り返すかどうか設定/取得するメソッドです。  

```ruby
# テキストを折り返す設定にする
text_sprite.wordwrap true

# 折り返すかどうか取得する
my_wordwrap = text_sprite.wordwrap
```

* 第一引数：折り返すかどうか（true/false）

## wordwrap_widthメソッド

テキストプライトに表示する文章を折り返す際、折り返す幅（ピクセル数）を設定します。  

```ruby
# テキストの折り返す幅を400pxにする
text_sprite.wordwrap_width 400

# 折り返す幅を取得する
my_wordwrap_width = text_sprite.wordwrap_width
```

* 第一引数：折り返し幅（ピクセル数）
