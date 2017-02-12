# スプライトの当たり判定について

## collisionメソッド

スプライト同士（スプライトとレイヤー、レイヤー同士も可能）の当たり判定を記述するメソッドです。

※ 本メソッドはシーンのupdateブロックのみで使えます。

```ruby
# player_charaスプライトとlayer_01に所属するスプライトの当たり判定処理を行います
# 通行チェックに使えます
collision player_chara, layer_01

# 当たり判定が発生したときの処理を記述することもできます
collision player_chara, layer_01 do
  # ここに処理を記述できます
  # このブロックは、当たり判定が発生したときのみ実行されます
end
```

* 制限
  * レイヤーに所属していないスプライトに当たり判定が発生しない場合があります
    * これはバグで、将来的に修正される可能性があります
  * 

## collision_pairメソッド

衝突したスプライトのペアを取得するメソッドです。

※ 本メソッドはcollisionブロックの中でのみ使えます。

```ruby
collision(player_sprite, jiisan_layer) do
  # 取得できるスプライトの順番とcollisionメソッドに渡した引数の順番は対応付くことに注意してください
  obj1, obj2 = collision_pair
  
  obj2.destroy
end
```
