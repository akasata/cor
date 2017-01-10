# ポインティングデバイス（マウスやタッチパネル）

## 座標の取得(pointer.x, pointer.y)

シーンのupdate句では、ポインティングデバイスの座標を取得することができます。  

```ruby
update do
  debug_log "Mouse: #{pointer.x}, #{pointer.y}"
end
```

* mouse.x, mouse.yと記載することもできます

## マウスクリック/タップの取得(pointer.down?)


```ruby
update do
  if pointer.down?
    # ここに処理を記述
  end
end
```

* mouse.down?と記載することもできます

## スプライトがタップされているかどうか

特定のスプライトがタップされているかどうか取得するには、スプライトのtap_down?メソッドを使うことができます。  

```ruby
sprite = put_sprite 'chara' do
  position 300, 300
end

if sprite.tap_down?
  # ここに処理を記述します
end
```
