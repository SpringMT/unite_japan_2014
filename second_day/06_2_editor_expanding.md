# Editor 拡張マニアクス 2014(立ち見だったので写真なし)
* untiy package は tar gzip
* フォルダはGUI
* .icon.pngにするとpreviewに表示される
* web上で配布
* エディタ拡張マニアクス、満席で立ち見も出始めてる。やばげ。本日の資料その他は j.mp/1qjccGr に全部上がってるから見れない人大丈夫よー。
* unitypackage を tar で解凍して、中に .icon.png を突っ込んであげるとプレビュー画像を表示できる
* unitypackageはtzipになってるので、解凍してなかに.icon.pngを入れて圧縮し直せば良いとのことw 現状のUnityちゃんパッケージはそうしてるとのこと

* resourcesフォルダにスクリプタブルオブジェクト
* ScriptTemplatesを作ってにテンプレートを置いておく

* GlobalGameManager。ゲーム全体の設定の置き場としてつかえるよというもの。Project Settingへのアクセスなどが大変だったので作って見たとのこと。
* ScriptTemplateというフォルダにテンプレートのソースを入れておくと、メニューからそのテンプレートをつかった雛形ソースの生成ができる。テンプレートの書式はUnityの中でつかってるテンプレートと合わせてねとのこと
* AssetDatabase.ImportAsset

* MultiSpriteEditor。幾つかのスプライトを一気にスライスしたいということがある。一気に設定できるようにしたもの
* SyncCamera。Sceneのカメラを動かすことでゲームカメラ操作できるというか同期できるもの。シーンカメラを動かしてゲームカメラにキーを打ってという感じで作業をしていける
* Scene のカメラに Game のカメラが追従する。ポチポチとアニメーションのキーフレーム打てば良い感じのカメラワークが出来るとのこと。ただし API は非公式

* OverWritter
* meta dataを更新しないといけない
* OverWriter。Unityのプロジェクトへドラッグで同名のファイルを入れると1がついた別の名前にされてしまう。これを何とかしてミスを減らしたい
* Hoge.png のテクスチャがある状態で新しい Hoge.png を突っ込んだ時に Hoge 1 になっちゃって消すと Missing になっちゃう問題を上書きすることで解決
* チェックした拡張子のファイルは同名で入れたら上書きを許可するというもの。
* File.Copyで上書きする
* 重複する -> 上書き -> 元を消す -> import
* パターンは正規表現なので、考えて使ってね
* ただし〜_1というのが普通に使われているとやばいことになるのでファイル名規則に注意。

* prefab
* applyのボタンのしていること
* prefabの型はほしいなあ
* Prefab Extention、Prefab しかインスペクタで受け付けないようにしたり、複数の Prefab からなる GameObject の変更を一気に Apply 出来たりする
* prefabを強制的にいれなくてもよいか、これは外すかな
* でもこれは便利

* ReferenceViewer。特定のPrefabがどこのシーンの何で使われているかわかるようなものをつくったと。
* reflectionでいじってるのか
* 型の情報大切。Prefabはないから型と変数名だけで、PrefabかGameObjectなのかわからんことが多い。変数名工夫すりゃいいけどさ。安藤さん作ったPrefab型、これ使えば、インスタンス化する際、変数参照しなければいけないけれど、型で区別できるからいい
* ReordableList、Meanim の State とかで使われている ReordableList を利用して配列とかを簡単に並べ替えられる。現状 private だが Unity 5 から普通に使える


