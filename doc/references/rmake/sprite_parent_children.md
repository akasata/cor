# スプライトの親子関係について

スプライトに親子関係をつけることができます。
子スプライトは、親の移動・回転・拡大縮小に追従します。

CoRサンプル - 親子関係テスト
https://rmake.jp/games/30797/cor_example

## add_childメソッド

子スプライトを追加します。

```ruby
# スプライトを追加する
parent_sprite.add_child child_sprite
```

* 引数：子スプライト

## remove_childメソッド

子スプライトを削除します。削除された子スプライトは再利用することはできません。

```ruby
parent_sprite.remove_child child_sprite
```

* 引数：子スプライト

