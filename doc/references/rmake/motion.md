# モーションについて

## 定義

スプライトの定義時にモーションを定義することができます。

```ruby
sprite 'chara' do
  motion 'walk' do
    to params: {y: '+100', alpha: 0.5}, duration: 1000
    to params: {y: '-100', alpha: 1.0}, duration: 1000
    loop(true)
  end
end
```

### toメソッド

指定した位置に移動するメソッドです。

```ruby
# (400, 0)の位置に移動します。
motion 'move' do
  to params: {x: 400, y: 0}, duration: 1000
end
```

* params: モーションに渡す引数
  * x, y - 座標
    * '+100'や'-100'を指定することで相対的な位置を指定できます
* duration: モーションにかかる時間

### fromメソッド

現在位置に向かって移動する際に使うメソッドです。

```ruby
# (400, 0)の位置から現在位置に移動します。
motion 'appear' do
  from params: {x: 400, y: 0}, duration: 1000
end
```

* params: モーションに渡す引数
  * x, y - 座標
* duration: モーションにかかる時間

### loopメソッド

モーションを繰り返すかどうか設定するメソッドです。

```ruby
motion 'walk' do
  loop(true)
end
```

* 第一引数：モーションを繰り返すかどうか（true/false）

## モーションの開始：start_motionメソッド

配置したスプライトのモーションを開始するには、start_motionメソッドを使います。

```ruby
sprite = put_sprite 'chara' do
  position 300, 300
  frame_index 0
end

sprite.start_motion
```
