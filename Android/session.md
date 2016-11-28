# DevFest Kansai 2016 (Android)

## the Data Binding Library by Benoit Quenaudon (from Cybozu)
[サンプル](github.com/oldergod/DataBindingDemo)</br>
[スライド](https://goo.gl/Pr4kjj)

### Problem with Android
* findViewById, cast()

### Data Binding Library
あるとすごい便利!!</br>

### 使い方
buikd.gradleに書き込む

### View Binding
findViewByIdを一つにできる!!

### DataBindingLibrary:how
* Zero reflection
* 100% generated Java
</br>Readibilityが上がる!</br>

### Java Code Evaluation
XMLにラムダ式感覚でかける!

### Null Pointer Exception さようなら
XML一行でヌルポは大丈夫!!

### Android Studioとの相性
* Gradle Integration
* Syntax highlighting
* COde completion
* Can view/debug generated code
* use tools: for preview!!

### Easy to Start
* Can be applied to a unique part of your app
* Can use only some of Data Binding's feature

### Data Binding Rocks!!

## Android Wear 2.0 by 松岡謙治

### ウェアラブル幻滅期

### こんな未来は来ない
* スマフォに置き換わる

### なぜ必要か?
* 知りたい時に情報を知っている世界を作るため?
  * 手元にないこともある(スマホ)
  
### Watchの強み
* 投機的通知(本当に役に立つかわからない情報について)
* 緊急事態用の情報
* 確認用

### 変化点
* より軽量な通知　
* Wear単体での動作
* iOSとの対応

### Standalone app
* スマホ自体をいらなくて動くようにする.
  * 直接的にInternetに繋がる.
  
### 配布方法の変化
  Phone と Wearが分離する!!</br>
  MultipleAPKを使う! </br>
  Wear単独での動作を考える必要がある!
  
### Complications API
* スマートウォッチの文字盤に情報を表示できる.
  * 迅速に情報を見ることができる!
* watchface側で描画の責任をとる!

### 参考
[ここ](https://goo.gl/mY9nBV)
