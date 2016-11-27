# DevFest Kansai 2016 (Android)
## Back to the Custom View by 有山圭二 (シービス)
### カスタムビューとは
Androidにビルドツール付随のビューがある(TextView, etc...).</br>
####  カスタムビュー
デザインサポートライブラリーに付随</br>
ビルドツール付随のものは元をたどればandroid.view.Viewに行き着く</br>
カスタムビューも同じ!!</br>
onDrawの処理時間を抑える! Overrideを抑える!</br>
何らか必要があって自分でViewを弄るならCustom Viewを使う, と考えてもいい.
### カスタムビューがいらない時
* ボタンの外見を変えたい!
  * ReversedSeekBar
  * 内部ロジックは自分で作り直す　
### カスタムビューを作る時
* デザインを調整するだけでは無理な場合　
* アニメーション
  * 同期して動かす時　
* AspectRatioImageView
   * 縦横比を統一したいが, 横の値しかしっかり決めてない!!
### カスタムビューを作る上で知っておくといいこと
* しっかりコンストラクタを作る
* onSizedChangedでビューのサイズが決まるからしっかり```@Override```しておく!
* onTouchの返り値を意識する. (Defaultはfalse. trueにする)
* マルチタッチについては　ScaleGestureDetectorを使う!
  * onScaleBeginはTrueにする
* Double Touch Handlingを行う
  * API Level < 19の場合ScaleGestureDetectorCompatを使う　
### ジェスチャー検知
* GestureDetectorを使おう!! </br>
* スクロール量の計算はOverScrollerを使おう!</br>
* ScrollerでアニメーションするならInterpolator(補完)を意識する!
  * 非線形な変化をさせることが可能!!
### その他描画に関する注意　
* onDrawでの描画は16msに抑えること!!
* 描画可能なBitMapサイズには限界がある.
### Custom View or Fragment?
既存のViewを複数詰め込んで一つの処理をしたいなら, Fragment</br>
それ以外ならCustom View
### 非同期処理をカスタムビューに入れるのはいいのか?
カスタムビューの外でやるべき!! </br>
別にクラスを作ってその中でカスタムビューを支配できるような形にしたほうがいい!
## 動かす by 荒木佑一(Google Japan Developer Programs Engineer)
### 本日のテーマ
いかにアニメーションを動かすか!!</br>
Choreography
* ユーザーが操作を行う
* 画面表示が変わる.

[サンプル]("https://goo.gl/zaR6H2")
### AnimationとAnimatorの違い
#### 共通点
* View(とか)を動かす
* Java or XMLで定義, 生成できる
#### 違い
* Animation
  * API >= 1
  * View
  * 基本四つの組み合わせ
  * Gingerbread以前をサポートしたい時に使えばいい.
* Animator
  * API >= 11
  * 何でも
  * 対象にsetterがあれば動作は何でもできる.
### Animationの使い方
XMLで書き込んでそれを読み込んでViewを動かす. </br>
ただし, 元に戻る. 実際のViewの状態が変わるわけではない.
### どんなとこで使えるか
ViewSwitcherを使うといい!!
* TextSwitcher
* Activity間の遷移
```
overidePEndingTransition
```
で出入りの設定をする.
* Fragment
  * 上と同じ
### Animator
* ValueAnimator
  * 値を変化させるだけのシンプルなAnimator
  * あとは自分で何かをする
  * 初期値指定 必須
* ObjectAnimator(extends ValueAnimator)
  * 対象Targetに値を設定できる.
    * set何とかがいる
    * Viewの属性を変更しているので終わったらその状態のままになる.
  * 相手は何でもいい
  * 初期値指定 任意
それ以外はAnimatorではない.
### ViewPropertyAnimator
* Animatorを継承していない.  
* ObjectAnimatorと似ている
  * 簡単, 型安全
  * AnimatorSetで組み合わせられない
  * 勝手に始まる
### AnimateLayoutChanges
view追加/削除のアニメーションを勝手にやってくれる. </br>
### Transition
レイアウトの変更を自動的にアニメーションする(API>=14)</br>
#### beginDelayedTransition
アニメーションと連打を同期させる.
#### CustomTransition
カスタムで作ることができる. めっちゃ簡単らしい.
### まとめ
適切な機能を使う.
* AnimateLayoutChanges
* Transition
### バグがあれば
b.android.comに連絡する!</br>
スクショ動画があれば助かるそう...
### Splash画面
MainActivityのバックグラウンドに画像を入れておいて, それを数秒でもないINVISIBLEにするといい.</br>
Drawable Animationでググるといい!
