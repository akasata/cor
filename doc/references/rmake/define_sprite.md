# スプライト定義

## imageメソッド

スプライトの画像を設定するメソッドです。  
シーンのpreloadで設定した画像素材名を指定してください。

```ruby
sprite 'my_chara' do
  image 'my_chara_image'
end
```

* 第一引数：画像素材名

## originメソッド

スプライトの原点を左上にするか、中心にするか設定するメソッドです。  
デフォルトは中心です。

```ruby
sprite 'baku' do
  origin :center
end
```

* 第一引数：「:center」か「:left_top」を指定してください

## animationメソッド

簡易的なアニメーションを設定するメソッドです。  

```ruby
sprite 'chara' do
  animation 'up', [6, 7], 10, true
  animation 'down', [0, 1], 10, true
  animation 'left', [2, 3], 10, true
  animation 'right', [4, 5], 10, true
end
```

* 引数
  * アニメーション名
  * アニメーションに設定するフレーム配列
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