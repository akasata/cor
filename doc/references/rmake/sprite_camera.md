# スプライトにおけるカメラについて

スプライト（テキストスプライトを含む）のカメラに対する動作を設定することができます。

## camera_target!メソッド

スプライトを、カメラで追うか設定するメソッドです。  
このメソッドを使うと、このスプライトが動き回ったときに画面も追従するかどうか設定することができます。

```ruby
sprite.camera_target!
```

* 第一引数：カメラで追うかどうか(true/false)
  * 省略可。省略した場合はtrueが入ります

## camera_fixed!メソッド

スプライトをカメラから独立させるかどうか設定するメソッドです。  
このメソッドを使うと、カメラが動き回っても画面上に動かずに表示されるスプライトを設定できます。  
テキストであればスコアの表示、スプライトであればメニューボタンのように動いては困るものに使うと良いでしょう。

```ruby
sprite.camera_fixed!
```

* 第一引数：カメラか独立するかどうか(true/false)
  * 省略可。省略した場合はtrueが入ります
