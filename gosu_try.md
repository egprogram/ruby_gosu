# アプリ作成

# Gosuでゲームを開発入門の日本語コード

> ## app.rb

- Gosu::Windowクラスを継承した「Tutorialクラス」を作成

  - ### メソッド
    - initialize

    - update

    - draw

    - Tutorial.new.show

- Tutorialのインスタンスにshowメソッドを使用したものを宣言

> ## player.rb

- 'gosu'をrequire

- Playerクラスを作成

  - ### メソッド

    - initialize
      - インスタンス変数 imageに、Gosu::Imageのインスタンスを生成(引数："starfighter.bmp")
      - インスタンス変数 x, y, vel_x, vel_y, angelそれぞれ 0.0を代入したものを宣言
      - インスタンス変数 score に 0を代入したものを宣言

    - warp(x, y)
      - インスタンス変数x, y にそれぞれ引数x, yを代入

    - turn_left
      - @angleを-4.5

    - turn_right
      - @angleを+4.5

    - accelerate
      - @vel_x Gosuモジュールのoffset_xメソッド(@angle, 0.5)を代入
      - @vel_y Gosuモジュールのoffset_xメソッド(@angle, 0.5)を代入


    - move
      - @x に @vel_xをたす
      - @y に @vel_yをたす
      - @x に 640で割った余りを代入
      - @y に 480で割った余りを代入
      - @vel_x に 0.95をかける
      - @vel_y に 0.95をかける

    - draw
      - @imageのdraw_rotメソッド(@x ,@y, @angle)

    - score
      - @scoreを返り値

    - collect_stars
      - rejectt!で、変数starsの偽でない要素を集めた配列を返す。
        - もし、Gosuモジュールのdistanceメソッド(@x, @y, star.x, star,y)が 35より小さかった場合
          - @scoreに10を足す。
        - そうではない場合
          - falseを返す。


> ## star.rb

- 'gosu'をrequire

- Starクラスを作成

  - attr_reader(インスタンス変数（x,y）を参照できるようにする)

  - ### メソッド

    - initialize(animation)
      - インスタンス変数animation に 引数のanimationを代入
      - インスタンス変数color に Gosu::Color::BLACKのコピー(オブジェクト)を代入
      - @colorのredに、0から216の整数どれかを+40を返す。
      - @colorのgreenに、0から216の整数どれかを+40を返す。
      - @colorのblueに、0から216の整数どれかを+40を返す。
      - (RGB値とは、色を指定するための値で、赤,緑,青の各色を0~255の値で指定すると値の組み合わせによって色が決まる。)
      - インスタンス変数xに、0~1に640をかけたものを代入
      - インスタンス変数yに、0~1に480をかけたものを代入
      - (randメソッドの引数を指定しない場合は、擬似乱数の浮動小数展を返す。)

    - draw
      - 変数imgに@animationのキー(Gosu.milliseconds / 100 % @animtation.size)の値を代入
      - imgに紐づいているdrawメソッドを使用 , 引数に(@x - img.width / 2.0 - img.height / 2.0, 1, 1, 1, @color, :add)


