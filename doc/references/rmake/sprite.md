# スプライト

## シーンのcreate/updateブロックにおけるput_spriteメソッド

スプライト定義で定義したスプライトを配置することができます。  

* 第一引数：スプライト定義名
* 戻り値：スプライト

```ruby
sprite = put_sprite 'chara' do
  position 400, 400
  frame_index 0
end
```

上記と下記は同じです。好きな書き方をしてください。

```ruby
sprite = put_sprite 'chara'
sprite.position 400, 400
sprite.frame_index 0
```

## positionメソッド

スプライトに座標を設定/取得するメソッドです。

```ruby
# スプライトの座標を(x, y) = (100, 150)に設定する
sprite.position 100, 150

# スプライトの座標を取得することもできる
# pos = [x, y]
pos = sprite.position
```

* 引数（省略可、ただし、引数を片方もしくは両方省略すると、値をセットしません）
  * x座標
  * y座標
* 戻り値：array（x, y）

## angle/rotationメソッド

スプライトの回転を設定/取得するメソッドです。

```ruby
# 180度回転させる
sprite.angle 180

# 回転角度を取得
angle = sprite.angle

# 180度回転させる(ラジアンで設定)
# (180 × 3.14) ÷ 180 = 3.141592...
sprite.rotation 3.141592

# 回転角度をラジアンで取得
rotation = sprite.rotation
```

* 第一引数：回転角度

## frame_indexメソッド

表示するフレームを決定します。  
frame_indexを指定するためには、画像読み込み時にフレーム数などを設定しておく必要があります。    
詳しくは、シーンの定義のpreloadブロックのimageメソッドを参照してください。

```ruby
# 10番目のフレームを表示する
sprite.frame_index 10

# frame_indexを取得する
frame_index = sprite.frame_index
```

* 第一引数：フレーム番号

## scaleメソッド

拡大縮小率を設定/取得するメソッドです。 

```ruby
# 横を0.5倍、縦を0.75倍に設定する
sprite.scale 0.5, 0.75

# scaleを取得する
scale = sprite.scale
```

* 第一引数：拡大縮小率（1.0が等倍です）

## tap_down?メソッド

ポインティングデバイス（マウスやタッチパネル）でタップされているかどうか取得するメソッドです。  

```ruby
if sprite.tap_down?
  # ここに処理を記述します
end
```

* 戻り値：boolean(true/false)

## src_rectメソッド

スプライトに割り当てられている画像のどの部分を表示するか直接指定するメソッドです。  
frame_indexメソッドでは対応しきれないケースに使ってください。

```ruby
# 元画像の(x, y, width, height) = (0, 32, 200, 200)の部分を表示する
sprite.src_rect(0, 32, 200, 200)

# 設定されている表示領域を取得する
rect = sprite.src_rect
```

* 引数：整数値
  * x座標
  * y座標
  * width（幅）
  * height（高さ）
* 戻り値：array（x, y, width, height）
  * 設定されていない場合は、戻り値の配列の中身はすべてnilになります

## layer_indexメソッド

レイヤーに所属しているスプライトの場合、この値を設定すると重なり順を調整することができます。
layer_indexが大きければ大きいほど手前に表示されます。

layer_indexが同じスプライトの場合、どちらが手前に表示されるかは仕様としては決まっていません。  
重なり順を厳密に調整したい場合は、layer_indexが同じ値のスプライトを作らないようにしてください。

```ruby
# layer_index
sprite.layer_index 5
```
* 引数：レイヤーインデックス（整数）

## show_debug_bodyメソッド

画面上にスプライトのデバッグ情報（当たり判定の領域）を表示します。  
renderブロックに記述してください。

```ruby
render do
  sprite.show_debug_body
end
```

* 引数：なし
* 表示されるデバッグ情報
  * 当たり判定の領域（薄い緑色）

## show_debug_infoメソッド

画面上にスプライトのデバッグ情報を表示します。  
renderブロックに記述してください。

```ruby
render do
  sprite.show_debug_info
end
```

* 引数：なし
* 表示されるデバッグ情報
  * 詳細情報を画面上部に文字で表示
