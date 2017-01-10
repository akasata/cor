# アニメーション

## 定義

スプライトに簡易的なアニメーションを設定するには、animationメソッドを使います。  

```ruby
sprite 'chara' do
  # 省略

  # 歩行アニメーションの定義
  animation 'up', [6, 7], 10, true
  animation 'down', [0, 1], 10, true
  animation 'left', [2, 3], 10, true
  animation 'right', [4, 5], 10, true
end
```

* 引数
  * アニメーション名
  * アニメーションに設定するフレームの配列
  * アニメーションの間隔となるフレーム数（デフォルト10、省略可）
  * ループするかどうか（デフォルトtrue、省略可）

アニメーションを指定するために、画像読み込み時にフレーム数などを設定しておく必要があります。  
詳しくは、シーンの定義を参照してください。

```ruby
scene 'start' do

  # 画像や音楽などのロード  
  preload do 
    image 'chara_00', id: 315474, frame_size: [32, 32]
    image 'bakuhatsu', id: 315475, frame_size: [96, 96], frame_pattern: 16
  end

  # 以下略...
```
## アニメーションの開始: start_animationメソッド

アニメーションを開始するには、start_animationメソッドを使います。

```ruby
sprite = put_sprite 'chara' do
  position 300, 300
  frame_index 0
end

sprite.start_animation('up')
```
