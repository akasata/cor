# 音楽と効果音: RmakeSoundクラス

音楽と効果音を扱うクラスです。  
Rmakeでは、音楽は無限再生され、効果音は一度しか再生されないものとして扱われますが、基本的には同一のものです。

## 音楽/効果音の定義

```ruby
scene 'start' do
  my_sound = nil
  my_music = nil
  
  preload do 
    music 'main_music', id: 40
    sound 'sound_bakuhatu_1', id: 43
  end
  
  create do
    my_sound = add_sound('sound_bakuhatu_1')
    my_music = add_music('main_music')
  end
  
end
```

## play/stop

音楽を再生、停止します。

```ruby
# 音楽を再生する
my_music.play

# 音楽を停止する
my_music.stop

# 効果音を再生する
my_sound.play

# 効果音を停止する
my_sound.stop
```

## pause/resume

音楽を一時停止、再開します。

```ruby
# 音楽を一時停止する
my_music.pause

# 音楽を再開する
my_music.resume

# 効果音を一時停止する
my_sound.pause

# 効果音を再開する
my_sound.resume
```
