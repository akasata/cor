# シーンについて

## シーンの定義

CoRでは、ゲームの場面を、シーンという概念を用いて記述します。  
シーンは以下の4つの要素で成り立っています。

* preload: 素材などの読み込みを記述するブロックです
* create: 素材の読み込みが完了すると呼び出される、シーンの初期化処理を記述するブロックです
* update: メインループです。ゲームの実際の処理を記述するブロックです
* render: 描画処理を記述するブロックです。描画処理はupdateにまとめて書いても構いませんが、分けることによって処理を止めても絵は動くというようなことも可能になります

```ruby
# startという名前のシーンを定義します
scene 'start' do
  preload do 
    # ここに処理
  end
  
  create do
    # ここに処理
  end
  
  update do
    # ここに処理
  end
  
  render do
    # ここに処理
  end
end

# シーンを開始する
start_scene "start"
```

## シーンの変更：change_scene

シーンを変更するメソッドです。

```ruby
scene 'start' do
  update do
    # Zキーを押すと現在のシーンが終了してsecondというシーンが開始される
    if keyboard.down?('Z')
      change_scene "second"
    end
  end
end
```

* 第一引数：開始するシーン名

## preload

シーンの素材などの読み込みを記述するブロックです。  
素材の読み込みはここでしか行えません。注意してください。

```ruby
scene 'start' do
  # preloadは素材などの読み込みを記述する場所です
  preload do 
    # id: 10613の画像を読み込み、main_backという名前をつける
    image 'main_back', id: 10613
    
    # 音楽を読み込む
    music 'main_music', id: 191
    
    # 効果音を読み込む
    sound 'sound_bakuhatu_1', id: 10477
  end

end
```

preloadブロックでは、以下のメソッドを呼び出すことができます。

* image メソッド
* music メソッド
* sound メソッド

## create

素材の読み込みが完了すると呼び出される、シーンの初期化処理を記述するブロックです。  
createブロックで記述する内容は、updateで記述しても構いません。

```ruby
scene 'start' do
  create do
    # スプライトを配置する
    bg_sprite = put_sprite 'background-sprite' do
      # 位置
      position 400, 300
      
      # 回転
      angle 270
      
      # 回転をラジアンで記述したい場合は以下のように書いてください
      # rotation 4.71239
      
      # スケール（拡大・縮小）
      scale 0.5, 0.5
    end
    
    # 文字を配置する
    text_sprite = put_text 'basic-text' do
      position 400, 50
      text 'Hello Rmake! こんにちは、Rmake！'
    end
    
    # 効果音を作成して鳴らす
    my_sound = add_sound('sound_bakuhatu_1')
    my_sound.play
    
    # 音楽を作成して鳴らす
    my_music = add_music('main_music')
    my_music.play
  end
end
```

## update

メインループです。ゲームの実際の処理を記述するブロックです。

```ruby
scene 'start' do
  update do
    # Aキーを押すと、効果音がなる
    if keyboard.down?('A')
      my_sound.play
    end
  end
end
```


## render

描画処理を記述するブロックです。  
描画処理はupdateにまとめて書いても構いませんが、分けることによって処理を止めても絵は動くというようなことも可能になります。

```ruby
scene 'start' do
  render do
    # スプライトが回転し続ける
    bg_sprite.angle (bg_sprite.angle() + 2) % 360
  end
end
```

