# 物理シミュレーションについて

Rmakeには、2Dゲーム向けの簡易的な物理運動シミュレーションが搭載されています。

* 当たり判定
* 速度
* 重力
* 跳ね返り係数

## 当たり判定について

[こちらのページ](collision.md)を参照してください。

## 速度について

スプライトに速度を与えます。

```ruby
# X, Y軸上に毎フレーム(4, 6)の速度を与える
sprite.velocity(4, 6)

# X軸のみ
sprite.velocity(4, nil)

# Y軸のみ
sprite.velocity(nil, 6)
```

## 重力について

スプライトに重力加速度を設定することができます。

```ruby
# X, Y軸上に毎フレーム(4, 6)の加速度を与える
sprite.gravity(4, 6)

# X軸のみ
sprite.gravity(4, nil)

# Y軸のみ
sprite.gravity(nil, 6)
```

## 跳ね返り係数について

スプライトに跳ね返り係数を与えることができます。

```ruby
# X, Y軸上に(0.9, 0.8)の跳ね返り係数を与える
sprite.bounce(0.9, 0.8)

# X軸のみ
sprite.bounce(0.9, nil)

# Y軸のみ
sprite.bounce(nil, 0.8)
```