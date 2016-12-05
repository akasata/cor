# サンプルについて

以下で公開されているサンプルのソースコードです。

https://rmake-labo.com/games/30282/limited_play  
ID: core  
Pass: core  

```ruby
scene 'start' do
  update_count = 0
  text_sprite = nil
  bg_sprite = nil
  character_sprite = nil
  character_frame_offset = 0
  baku = nil
  baku_frame = 0
  
  my_sound = nil
  my_music = nil
  
  preload do 
    debug_log "do preload"
    
    image 'chara_00', id: 315474, frame_size: [32, 32]
    image 'bakuhatsu', id: 315475, frame_size: [96, 96], frame_pattern: 16
    
    music 'main_music', id: 40
    sound 'sound_bakuhatu_1', id: 43
  end
  
  create do
    debug_log "do create"
    
    character_sprite = put_sprite 'chara' do
      position 400, 400
      frame_index 0
    end

    text_sprite = put_text 'basic-text' do
      position 400, 50
      text 'Hello Rmake!'
    end
    
    my_sound = add_sound('sound_bakuhatu_1')

    my_music = add_music('main_music')
    my_music.play
  end
  
  update do
    if keyboard.down?('Z')
      my_sound.play
      unless baku
        baku_frame = 0
        pos = character_sprite.position
        baku = put_sprite 'baku' do
          position pos[0], pos[1]
          scale 2.0, 2.0
          frame_index 0
        end
      end
    end
    
    if keyboard.down?('LEFT')
      pos = character_sprite.position
      character_sprite.position pos[0] - 1, pos[1]
      character_frame_offset = 2
    end
    
    if keyboard.down?('DOWN')
      pos = character_sprite.position
      character_sprite.position pos[0], pos[1] + 1
      character_frame_offset = 0
    end
    
    if keyboard.down?('RIGHT')
      pos = character_sprite.position
      character_sprite.position pos[0] + 1, pos[1]
      character_frame_offset = 4
    end
    
    if keyboard.down?('UP')
      pos = character_sprite.position
      character_sprite.position pos[0], pos[1] -1
      character_frame_offset = 6
    end
    
    if keyboard.down_keys?('A', 'SHIFT')
      debug_log("KeyDown: SHIFT + A")
    end
    
    if baku
      baku_frame += 1
      if baku_frame > 15
        baku.destroy
        baku = nil
        baku_frame = 0
      else
        baku.frame_index baku_frame
      end
    end
    
    character_sprite.frame_index (character_frame_offset + ((update_count / 20).to_i + 1) % 2)
    
    update_count += 1
  end
  
  render do
    # bg_sprite.angle (bg_sprite.angle() + 2) % 360
  end
  
end

start_scene "start"

sprite 'chara' do
  image 'chara_00'
  origin :center
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

```
