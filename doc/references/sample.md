# サンプルについて

以下で公開されているサンプルのソースコードです。

https://rmake-labo.com/games/30282/limited_play  
ID: core  
Pass: core  

```ruby
scene 'start' do
  # シーン内で使う変数の定義
  text_sprite = nil
  player_sprite = nil
  baku = nil

  bg_layer = nil
  player_layer = nil
  chara_layer = nil
  
  my_sound = nil
  my_music = nil

  # 画像や音楽などのロード  
  preload do 
    debug_log "do preload"
    
    image 'chara_00', id: 315474, frame_size: [32, 32]
    image 'chara_01', id: 316078, frame_size: [32, 32]
    image 'bakuhatsu', id: 315475, frame_size: [96, 96], frame_pattern: 16
    
    music 'main_music', id: 40
    sound 'sound_bakuhatu_1', id: 43
  end
  
  # 画像などのロード後に実行される初期化処理
  create do
    debug_log "do create"
    
    # レイヤーの初期化
    bg_layer = add_layer
    player_layer = add_layer
    chara_layer = add_layer
    
    # プレイヤーキャラの初期化
    player_sprite = put_sprite 'chara' do
      position 400, 400
      frame_index 0
    end
    
    player_sprite.start_animation('up')
    player_layer.add player_sprite
    
    # プレイヤー以外のキャラクタの配置
    10.times do |i|
      jijii_sprite = put_sprite 'chara_jijii' do
        position 100 + i * 48, 300
        frame_index 0
      end
      
      jijii_sprite.start_animation('down')
      
      chara_layer.add jijii_sprite
    end
    
    # テキストの配置
    text_sprite = put_text 'basic-text' do
      position 400, 50
      text 'Hello Rmake!'
    end
    
    # 効果音の準備
    my_sound = add_sound('sound_bakuhatu_1')
    
    # 音楽の準備と再生開始
    my_music = add_music('main_music')
    my_music.play
  end
  
  update do
    # Zキーをおした時
    if keyboard.down?('Z')
      # 効果音の再生
      my_sound.play
      
      # 爆発アニメーションの開始
      baku = start_bakuhatsu(self, baku, player_sprite.position)
    end
    
    # プレイヤーとキャタクタレイヤの当たり判定の処理
    collision(player_sprite, chara_layer) do
      # 衝突したスプライトのペアを取得
      # 取得できるスプライトの順番とcollisionメソッドに渡した引数の順番は対応付くことに注意
      obj1, obj2 = collision_pair
      
      # 爆発アニメーションの開始
      baku = start_bakuhatsu(self, baku, obj2.position, my_sound)
      
      # プレイヤーに当たるとキャラクタは消滅する
      obj2.destroy
    end
    
    # カーソルキーをおした時の処理
    
    # キャラクターがカーソルキーの方向に向いて、向いた方向に移動する
    if keyboard.down?('LEFT')
      pos = player_sprite.position
      player_sprite.position pos[0] - 1, pos[1]
      player_sprite.start_animation('left')
    end
    
    if keyboard.down?('DOWN')
      pos = player_sprite.position
      player_sprite.position pos[0], pos[1] + 1
      player_sprite.start_animation('down')
    end
    
    if keyboard.down?('RIGHT')
      pos = player_sprite.position
      player_sprite.position pos[0] + 1, pos[1]
      player_sprite.start_animation('right')
    end
    
    if keyboard.down?('UP')
      pos = player_sprite.position
      player_sprite.position pos[0], pos[1] -1
      player_sprite.start_animation('up')
    end
    
    # SHIFT+Aを押すと、デバッグログに押したことを書き込む
    if keyboard.down_keys?('A', 'SHIFT')
      debug_log("KeyDown: SHIFT + A")
    end

    # 爆発アニメーションが終わったらスプライトを消去
    # frame_indexを使って直接的に操作
    # 面倒なので、アニメーション終了イベントを作るかもしれない
    if baku
      if baku.frame_index >= 15
        baku.destroy
        baku = nil
      else
        baku.frame_index(baku.frame_index + 1)
      end
    end
  end
  
  render do
  end
  
end

start_scene "start"

sprite 'chara' do
  image 'chara_00'
  origin :center
  
  animation 'up', [6, 7], 10, true
  animation 'down', [0, 1], 10, true
  animation 'left', [2, 3], 10, true
  animation 'right', [4, 5], 10, true
end

sprite 'chara_jijii' do
  image 'chara_01'
  origin :center
  
  animation 'up', [6, 7], 10, true
  animation 'down', [0, 1], 10, true
  animation 'left', [2, 3], 10, true
  animation 'right', [4, 5], 10, true
end

sprite 'baku' do
  image 'bakuhatsu'
  origin :center
end

text 'basic-text' do
  origin :center
  font_size 65
  color '#FF0088'
end

def start_bakuhatsu(scene, old_baku, pos, sound = nil)
  if old_baku
    old_baku.destroy
    old_baku = nil
  end
  
  if sound
    sound.play
  end
    
  result = scene.put_sprite 'baku' do
    position pos[0], pos[1]
    scale 2.0, 2.0
    frame_index 0
  end
  
  return result
end

```
