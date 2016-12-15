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

```ruby
```
