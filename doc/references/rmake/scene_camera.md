# シーンにおけるカメラについて

## camera_positionメソッド

カメラの位置を設定するメソッドです。

```ruby
create do
  # カメラの左上の位置を(100, 100)に設定する
  camera_position 100, 100
end
```

* 引数
  * x座標（pixel）
  * y座標（pixel）

## world_resizeメソッド

カメラのみで使うメソッドではありませんが、世界の広さを設定します。  
カメラの有効範囲となります。

```ruby
create do
  # 世界の広さを(6000, 1000)に設定する
  world_resize(6000, 1000)
end
```

* 引数
  * 幅（pixel）
  * 高さ（pixel）
