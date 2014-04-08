## Unity GUI
* 新しGUIシステムの紹介
* ボタンを回転とかも難しい 体裁も良くない
* スクリプトを書かなくてもそれなりによく見えるように

world space 
screen space -> 今までのNGUIぽいな
screenサイズ、全ての上に乗っかって

Canvas。ワールドスペースとスクリーンスペースの2つの座標系がある。スクリーンスペースの場合は画面の上におかぶさって描画される #unitej


Canvasはwidgetのようなものか
CanvasってNGUIのPanelみたいなもんか

今のはworld space
Textureの上に文字がレンダリングできる
ワールドスペースのCanvasはそれ自体がオブジェクトとして移動や回転したりできるもの。 #unitej

screen space canvas
ゲームの上に重なって表示される
ゲームビューに比例して大きさが変わる
3Dの視点なし

スクリーンスペースCanvasはゲーム画面のサイズによってサイズが変わるもの。
むむむ、今ヒエラルキー上のオブジェクトをD&Dで並び替えてGUIの前後関係を入れ替えたけど、ヒエラルキー上の並び順はオブジェクト名依存じゃなくなったのか？

ルートオブジェクトにキャンバスコンポーネントを適用したものがいて、ワールドスペース/スクリーンスペースどちらにもおける。3D 的な視点が欲しい場合はワールド。描画順はヒエラルキー #unitej


High levelでできること
simpleなアニメーsジョンを適用できる

RectTransform。unity4.6からのコンポーネントで、Canvas上に配置するのに使うが、自動で伸ばしたりなどの指定ができる。（これよくわからんやつだったよな #unitej

REctMove -> world spaceであれば、リサイズできる scaleは影響はうけず、高さ、幅の数字が変わる

RectTransformツールをつかうと、GUIのCanvasサイズを変更するような操作ができる。回転もできる。これによってサイズが変更されるとGUIの中に乗っているものは再レイアウトされてスケーリングされるわけではない。スケールしたい場合はスケールをつかって #unitej

Elementのlayout

rect transformの使い方
相対位置 ancher positionをいじれるのか
アンカリングと相対的な位置を操作可能
RectTransformコンポーネント左上にアンカーとどこを伸ばすなどの指定を選択できる。これによってリサイズに応じた加工の指定ができる #unitej

Rect Transformにはx, y, z, Width, Height, Anchors, Pivot, Rotation, Scaleが。レイアウトはInspector上でかなり柔軟に編集できるようになったっぽい。 #ugui #unitej
paddingなどもSceneビュー上で可視化されてかなり使いやすそう。 #ugui #unitej

NGUIだなあ
絶対値、相対値を自由にできている、これもNGUIをベースにしているなあ

パディング調整の際にどこの値が変わるのか画面に出てくれるのもいいな #unitej
固定サイズは使わない
アライメントを適切に設定する
アンカリング

uGUI見てる。UnityもAndroidのレイアウトやiOSのAutoLayoutみたいな概念になりつつあるなぁ。 これが時代の潮流ぽい。座標指定の時代は終わりつつある。 #unitej

Anchor Presets で相対位置（中央配置等）で配置できたり、Stretch 設定して親のサイズに追従させたり、Padding 設定してレイアウトできる。 しかも GUI でイイ感じに表示してくれて分かりやすい。#unitej

uGUI、アンカーは必ず親を見るみたいだなぁ。座標制御と、描画順がどちらも親子関係に依存してるから、NGUIと比べていくつかの機能が隠されているような印象を受けてしまう(；´∀｀)　まぁグラフィッカー的には自由度が高すぎても困るよね！

グリッドで適切なサイズで埋めることも出来る。CSS で float 設定したみたいな感じ。 #unitej

自動レイアウトについて。指定した範囲にアイテムを並べるようなことを自動でやってくれる。リサイズに応じてちゃんと並び直してくれる。 #unitej

AutoLayout
グリッドが自動的に埋まる

Drawing controll
imageの紐付け
アスペクト比変更せずに拡大できる
sliced -> imageのはじのpixelを維持する

sprite editor スライシング
Image コンポーネントの Image Type を変更すると、Width/Height でそのまま変形させたり、アス比保ったり、Sliced でスプライトエディタから 9-slice っぽく出来る #unitej

4.6ではSpriteEditorを拡張し、スプライトのスライス（9スライスね）の指定ができるようになった。 #unitej

custom materialの追加

rect transform テキストをひもづける
rich text rendering -> markupできる
buttonなどに付けられるText。Font自由に選べる上にRich Textも対応！ #unitej #ugui

Text コンポーネントは Alignment で簡単に配置できる。フォントの変更やマークアップ可能なリッチテキストも出来る、エフェクトも掛けれるしマテリアルも設定できる... #unitej

独自markup言語でAttributedTextっぽいのが簡単に使える。超すごい #unitej

新しいイベントを処理できる

state管理にmecanimとの統合が図られてる

Interaction Controller（Buttonなど）をコンポーネントとして付加すると、イベントハンドリングが出来る。例えば Button コンポーネントを付加するとホバーで色を変えたり SpriteSwap でステートに応じてスプライトを変えられる #unitej

ボタンのコンポーネントについて。Tintモードはステートに応じて色をかえる。SpriteSwapモードではスプライトを変える指定。AnimationModeはアニメーションが指定できるという感じみたい。 #unitej
キーボードの上下でも選択できるの良いな。#unitej

animation
mecanimとの統合
positionの変更をできる

mecanimが nested stateに対応
新しいメカニムはGUIに適用できたり、入れ子のステートも定義できる。 #unitej

アニメーションは大事。そこで Mecanim と密に統合した。キーフレームアニメーションを作成し、Button の Trigger で設定したステートを Mecanim 側に送ってリッチなアニメーションを GUI だけで簡単に設定できる #unitej
Animationについて。GUIとメカニムを深く統合した。ボタンのAnimationモードの場合は、アニメーションと合わせてステートの設定ができる。これによってメカニムにステートの変更が送信されて処理が変わるようにできる #unitej

秘密のコードはない、

自分の好きな、GUIを作れる

ドラッグ&ドロップコントローラを作るのも簡単。イベントシステムでインターフェースを継承すると OnDrag、OnPointerUp などでスクリプトをハンドル出来るようになる。例えば IDropHandler を継承すると OnDrop が使えるなど。 #unitej

ドラッグアンドドロップのスクリプトも想像通りのコードで安心した #unitej


## unity とフィジカル・コンピューティング
フィジカル・コンピューティング
istudio

フィジカル・コンピューティングとは
物理的な世界と仮想的な世界との間に対話を作り出す分野

トレッドミルに磁気センサー -> ardino -> unity
unityでは連動
写真
VjKit
センサーデータ解析 -> シリアル通信

地形の表現が難しい
OpenGLで実装 -> 重い 一番速度がでない OpenGLは使わないほうがよい

まあ、結構普通
グラフカメラとメインカメラの２つ用意

回転ローラーに磁気センサーで回転速度を取得

SXSWで発表した。。。。その話はいいかなあ。。。

広告だなあ
4/25 27 Digital Scramble


## アニメーションのはなし
Unityのアニメーションを作る
セルシスの人

(1)ACTIONを使ってアニメーション作成 (2) FBXで書き出してUnityで活用　(3) 3Dシーンを書き出してUnityで活用 #unitej

いい感じにつなげてくれる
ポーズの間を自動的に保管する

違和感なくキャラクターいじれる

ポーズを３つくらい置くだけで自然なアニメーションを作れる

ハンドセットアップ -> 簡単にモーション付けできる 15子も関節がある

動画をトレースできる 
ファンクションカーブ 動画を細かく調整できるインターフェースを作れる

kinectでモーションキャプチャできるようにしてある

clip stdio action
商用で使える ロイヤリティーフリー

3Dシーンを書き出して、unityに使える

キャラクターを作る
ボーンメーッシュの張替えもできる
夏以降のupdateの機能になる

スカート設定なんてのがあるのかwwww


## 2D
"Unity 2D common issues and how to solve them" 、やらないか T シャツww #unitej

問題解決
DLリンクがあるにでメモとかいらないよー

HD SD
異なる解像度で異なるプラットフォームで使う場合に使う
HD / SD は異なる解像度のスプライトを異なるプラットフォームで使うときの文言、低解像度のスプライトを Android、高解像度を Retina ディスプレイ等 #unitej

モバイルのビルドにデスクトップのビルフォニはいれたくないよね

HDとSDの問題。イメージクオリティ、メモリの問題、ビルドサイズの問題などがある。で、二つの方法がある。リソースフォルダを使う、あるいはアセットバンドルを使う、しかし利点と難点がある #unitej

低解像度のスプライト 128 pixel
SD と HDで名前が異なってファイルがある
物理的なファイルサイズが同じか確認する


SDのスプライトのサイズをHDと合わせるのはインスペクターのpixelToUnitに倍率を入れとく #unitej

以前使っていたresourceを開放する
resourceフォルダに入っている
Resourceフォルダを使う
Resource フォルダを利用した方法は、プロでもフリーでも使えるのが利点。具体的には hogehoge＠HD などと名前つけておいて、Editor スクリプトを書いてその切替をする。最後は Resources.UnloadUnusedAssets() を呼ぶ #unitej


asset bundleつかって unity5のみ
２つのフォルダが有る、 HD と SD
WWW使って取り込むのは変わらず

HD SDを分けるには、asset bundleを使うのがよい
bundleをする場合のスクリプトが4とはちがう
Dependencyiesを使う


sprite animation
コントローラーの再利用
resourceフォルダを使っている
同じ名前でspriteを作る
updateとlastupdateの間で行われることもあるから

LateUpdateを使う

re skin animationコンポーネントをつかうと、アトラス名を切り替えられるようになり他のキャラにできる。ここで何をやってるか、LateUpdateで指定のアトラスをロードして同名のスプライトに差し替えるコードを書いてる。 #unitej


quqter view
とtransformの中心点が下にある
アイソメトリックの例。 #unitej 縦の高さに応じてソートを切り替えられるようにした。スプライトのピボットが下にしてあるので、地面に並べるのに向いてる pic.twitter.com/qBLS0pxCm3

camra scale

2で割るのはわからない >_<
Unityの中の人が何故か2で割ると上手くと話してた2で割る理由は単純で orthographicSizeは半分のサイズで指定するという仕様だからです #unitej

スプライトのデフォルトシェーダーにsnap to pixel設定があり、これを有効にすると頂点がピクセルピッタリの位置になる。今回のスライドはこちら #unitej pic.twitter.com/ZpNiUz3yl9


## audioの話
unity5 

audioに対する push 

import
MP3はtargetからはずした　
Vorbis tremor decoder

メモリフットプリントが小さくなる

sweepトーン
ADPCM -> 


メモリ使用量はは大分落ちた

しまった写真撮りそこねた >_<

audio clipは小さくなった
non blokingでもよみこみ可能になった 後で写真探す

AudioClip周りのパフォーマンス改善。いまUnityでオーディオファイル読み込むの糞遅いからこっちは普通に期待大。 #unitej


audioのロードをディレイ出来る、メモリに読み込んだりストリームもできる、オーディオクリップそのものの軽量化、ブロッキングノンブロッキングのオーディオローダ #unitej

editorの中でstreaming

audoio mixer
音のカテゴリ化
editorでできる
playmode中にマスタリング作業がｄきえる

mixing, routing, mastering/ effect / グルーピング/ プレイモード中にオーディオの編集をする感じになる。 #unitej

DAWツール

audio mixerで出来ること：mixing, routing, mastering/ いろんなeffect / グルーピング/ そしてプレイモード中にオーディオの編集をする感じになる。 #unitej

アンビアンス
play中にmixレベルを調整できるのか そして保存されてる

Effectも調整出来る

DSP Effect
Atenuation
DSP
VU metering

C++ Cの
Native pluginがかける
パラメーターも設定できる

Effect
custom UI
音に対してeffectを追加する

snapshot

Unity 5のAudioMixer、相当機能豊富になってきて普通にサウンドエンジニアが入れるレベルになりそう、逆に普通のプロトタイプにはToo Much感じある。でも使い勝手は良さそうだな。#unitej

audio mixer : パラメタのスナップショットを取って、それをゲームプレイ中に遷移させていくことが可能。ゲームの進行に合わせて雰囲気を音環境から変える。  #unitej room1


transitionに合わせて音の切り替えができる
かなり簡単ににtransitionの設定ができる

mixerのコンポーネントをゲットして、エフェクトやらボリュームやらの変数をsetできる。ナイス。 #unitej

Ducking -> 周りの音が自動的に下がる
発話者の発言が聞こえるように、周りの環境音等を下げる

duckingの意味がやっと分かった。コンプレッサやミキシングのかけ方にパタンがあるのね #unitej

asset bundle まだないのか。。。

NAtive plugin コールバックとDLLができればOK

voice limittingは今後の対応

## unityでテスト
テスト自動化の目的
最小限のコストで
マシンんに移譲
副作用 -< テスト可能なコード ->  質が高いコード
細かく 分離　されていて 疎結合

テストは品質の契約
みなさんと、会社の契約

出荷しているコードが動くかを保証するにはテスト
テスト自動か

コードの変更に関わるコストは急速に拡大する
バグfix -> コードの変更


ゲームというのは高度なシミュレーター
機能ではない要件が多い グラフィックとは

ゲームは色々なアルゴリズム -> unit testはできる
実際のゲームでテストする必要はない

変更が起きる可能性が大きい
初期段階では予測不可能

会期の防止

ギャップがある
ゲームのテスト性

unityについて
bugレポートを発行するだけじゃなくて、再現コードを遅らせるよにする

テスト自動化 自動化ピラミッド 拡張性がひくい
テストについて
UI -> メンテナンすが難しい 書くのは簡単 -> 
Integration -> 
Unit -> 一番簡単 拡張性高い

Unit > Integration > UI  automation pyramid  =>  Scalable >>> Unscalable  #unitej #room1


unit test library

monoBahabireでテストを書くには？
-> 継承するのが難し
Unit Test Runner
Hanble onject pattern

モックしてるなあ

Monobehavireを継承していない

unit tesは早く 柔軟性に飛んでいるべき メモリ上で行うべき

gameObjectをinstantiateをする可能性があるが、なるべくするなとのこと

undo test runnner -> testrunnerできたobjectを削除する
テストコードでシーンを汚くするのは避けたい

runner Run on recompile -> 毎回実行
Run tests on a new scene -> runnerに新しいイーンで実行 シーンを開け直す

AutoSave もできる
Detail Box -> どうして失敗したかが表示される
うまく行ったテストを隠すとかのフィルターも用意されている

c# booでテスト可能 JSは？


Assertion Compnent

stateがある期間保持されているかとかのcheckをできる
variant 

Assertion -> speedのcheck
例外が発生するようになる

compareｒの設定
２つのオブジェクトを設定
自分で拡張してcompareを作れる
floatのcheckとか
比較したいオブジェクトはダイナミックリフレクションで指定

ダウンロードしてみた #unitej : Asset Store - Unity Test Tools assetstore.unity3d.com/#/content/13802

assertionが失敗すると例外

unityでテスト書きながらはやっていくか

コードのリリースビルド -> assetion削除したい
Assertion Exploerがある -> disableできる

Integration Test Runnner
シーンベースのテスト

テストのはいったオブジェクトを追加
timeoutのローディング
unit -> start exitのがわかりやすい
integration -> exitがわかりない -> exitの定義はしなければならない
IntegrationTestを呼ぶ
Pass と Failが入っている


CallTestingというのが用意されている
startでは、

suceed on assertion -> asertion　テストのassertionが１回でも呼ばれて成功すればOK

Expect excpetion ->  例外を無視する ただ結果をみることもできる

passingテスト failingテスト

特定のUnity Monobehaviourが呼び出すメソッドをフックして、テストを走らせる事が出来る。  たとえばUpdateが呼ばれたのをフックして、テストを走らせる。 通過したらPassを呼ぶ。など  #unitej #room1


platform runner
使っているplatformでのテストをしやすくする

どこにエラーがあるのか分かる

複数にシーンを選んで実行も可能
あわさった結果がでる

#### Batch runもある
テスト自動化 batch run
integration testは screenに表示したくない xmlで結果を確認できる
unityでは、もっと一般的な開発方法


assete storeで配布済み

documentation or japaneseもある
try !!

iOSにおけるビルド
android web playerではfailしない しかいiOSでfail
NUnitの実行ができない

iOSはテストしていないだとおおおお

UIテストはしない -> これはいいと思う
inputをテストしないほうがいいと思う -> 同意

#unitej　UnityTestTool、AssetStoreで無料公開中。ドキュメントは英語だけど、UnityJapanの方が日本語に翻訳してくれたらしい。　全然知らなかった、まずはチェックやな( ･ิω･ิ）

UnityTestToolはUIレベルのテスト自動化は対応外かー。できれば一連のゲームループを十数時間自動で走らせたいんだけど、やっぱり自動実行コードを自前で書いて埋め込まないといけないかー。 #unitej


## 新人
untiyに関するナレッジ
unityの教え方 んんんんん
まずい気がした、、、、

教え方かああ、、、


#Editor拡張
untiy package tar gzip

フォルダはGUI
.icon.pngにするとpreviewに表示される
web上で配布

エディタ拡張マニアクス、満席で立ち見も出始めてる。やばげ。本日の資料その他は j.mp/1qjccGr に全部上がってるから見れない人大丈夫よー。だって #unitej

unitypackage を tar で解凍して、中に .icon.png を突っ込んであげるとプレビュー画像を表示できる #unitej

unitypackageはtzipになってるので、解凍してなかに.icon.pngを入れて圧縮し直せば良いとのことw 現状のUnityちゃんパッケージはそうしてるとのことw #unitej


resourcesフォルダにスクリプタブルオブジェクト

黒魔法かー
ScriptTemplates
テンプレートを置いておく
辿れる

GlobalGameManager。ゲーム全体の設定の置き場としてつかえるよというもの。Project Settingへのアクセスなどが大変だったので作って見たとのこと。 #unitej

ScriptTemplateというフォルダにテンプレートのソースを入れておくと、メニューからそのテンプレートをつかった雛形ソースの生成ができる。テンプレートの書式はUnityの中でつかってるテンプレートと合わせてねとのこと #unitej

AssetDatabase.ImportAsset

非常に解り易い。ObjectのTypeとかで判定して何かするコード。  #unitej #room2

multi splite editor
MultiSpriteEditor。幾つかのスプライトを一気にスライスしたいということがある。一気に設定できるようにしたもの #unitej

sync camera

SyncCamera。Sceneのカメラを動かすことでゲームカメラ操作できるというか同期できるもの。シーンカメラを動かしてゲームカメラにキーを打ってという感じで作業をしていける #unitej

SceneView 

Scene のカメラに Game のカメラが追従する SyncCamera（github.com/anchan828/unit…）の、便利だ。ポチポチとアニメーションのキーフレーム打てば良い感じのカメラワークが出来るとのこと。ただし API は非公式 #unitej

OverWritter
meta dataを更新しないといけない
OverWriter。Unityのプロジェクトへドラッグで同名のファイルを入れると1がついた別の名前にされてしまう。これを何とかしてミスを減らしたい #unitej

Overwriter（github.com/anchan828/unit…）、Hoge.png のテクスチャがある状態で新しい Hoge.png を突っ込んだ時に Hoge 1 になっちゃって消すと Missing になっちゃう問題を上書きすることで解決、便利だ... #unitej

チェックした拡張子のファイルは同名で入れたら上書きを許可するというもの。（これいい！ #unitej

File.Copyで上書きする
重複する -> 上書き -> 元を消す -> import

パターンは正規表現なので、考えて使ってね
ただし〜_1というのが普通に使われているとやばいことになるのでファイル名規則に注意。 #unitej


* prefab
applyのボタンのしていること
prefabの型はほしいなあ
Prefab Extention（github.com/anchan828/unit…）、Prefab しかインスペクタで受け付けないようにしたり、複数の Prefab からなる GameObject の変更を一気に Apply 出来たりする #unitej

prefabを強制的にいれなくてもよいか、これは外すかな
でもこれは便利

ReferenceViewer。特定のPrefabがどこのシーンの何で使われているかわかるようなものをつくったと。 #unitej

reflectionでいじってるのか

unity5からは使える

asset bundleがuntiy5からかわる


型の情報大切。Prefabはないから型と変数名だけで、PrefabかGameObjectなのかわからんことが多い。変数名工夫すりゃいいけどさ。安藤さん作ったPrefab型、これ使えば、インスタンス化する際、変数参照しなければいけないけれど、型で区別できるからいい #unitej



ReordableList（github.com/anchan828/unit…）、Meanim の State とかで使われている ReordableList を利用して配列とかを簡単に並べ替えられる。現状 private だが Unity 5 から普通に使える #unitej

Editor拡張セッション。完全に安藤さんが作った素晴らしい機能の紹介セッションである( ･ิω･ิ）　まぁそこから何してるのかコード全文調べたり、使える部分コピペする自分には大満足な内容(*´∀｀)


## klab
Live2D SDK
CyberNoise

最近ではuntiyの問い合わせが多い
半分近く
Live2Dの採用作品は増えていて、現在は100作品以上とのこと。対応プラットフォームいろいろ（だいぶふえたなー。PSMとかcocos2d-xなんかも増えてるんだ #unitej

gumi WestはLive2Dつかってるんかー

Live2D SDK

無料で始められる

Live2dの動くミクさんとかすごく可愛いのだけど、写真とってもただの静止画のミクさんなのでなんとも。 ちなみにUnity版のLive2DはアセットじゃなくてただのDLL   #unitej

unity上では任意のタイミングで呼び出すだけ

本読んでねってこと
『詳しくは書籍の「Live2D Cubism モデリング&アニメーション」を買え、いいね？』 アッハイ  #unitej

ふつーにキーフレームを打って、そこを補完するモデルでアニメーション作るのかー。ここは簡単そう。 Live2Dも目新しい技術じゃないのにちゃんと知らなかったな。 モデリング部分がめんどくさそう  #unitej

アプリ開発
電子書籍とかナビゲーションシステムでも活用されている

僕とりんと

Live 2D Live -> リアルタイムで反映できる
動きをトレースしてくれる
リップシンク
kinectとつなげて動く

コード的には簡単で、ロードしてテクスチャアサインして、指定のモーションを再生させえるだけみたいな程度 #unitej

Microphoneクラスがあるのか





















わ！Mecanimぐじゃぐじゃや！やっぱ作りこむとこうなっちゃうんですね ( #unitej live at ustre.am/1bKAN)

Unity-for-PSMはライセンス的には個人に優しい代わりに、既存のPSM SDKの資産は使えなかったりサンドボックス化されてたりする。クロスプラットフォームなゲーム向き。VITAとPCとで同じタイトルを対戦プレイとか?? #unitej

あぁーやっぱりwindows専用(ほぼ)かpsmforUnityよ #unitej

## memo
これまでのUnityのWebデプロイはUnityWebPlayerが必要。ブラウザのプラグインなのでインストールが必要だった。これは2005年の当初からプラグインは作られていた。 #unitej

Qihoo360ブラウザにはバンドルされている。中国では有名とのこと。FacebookのSDKが統合されているのでFacebook上でゲームを再生するのに向いている。347ミリオンインストールがある。使われているのはアジアがメイン。 #unitej

これまでは 2005 年 からプラグイン方式を利用した Web Player ゲーム。これからは WebGL など HTML5 の台頭によりブラウザ自身で色々出来るようになったり、Google が NPAPI の打ち切りも決定したことを考慮する必要がある。 #unitej

WebGLでの実装について。WebGLはハードウェアによるアクセサレートのあるエンジン。APIはGLES2がベース。若干Javascriptによる制限はあるが大体同じ。 #unitej

現在Firefox、Chrome、IE、Operaが対応している。Safariはデフォでオフになってるが一応使える。 #unitej

どうやってWebGL対応をしていったか。WebGLはJavascriptなので何らかの方法でJavascriptへ変換しないとならない。エンジンはc＋＋だと、ユーザーコードはそれぞれの言語だ。 #unitej

emscripten 大好きです。 #unitej

WebGL API は JS なので、すべてのコードを JS 化する必要がある。そこで Emscripten を使って asm.js 形式の JS を吐き出させている #unitej
エンジンがJSにコンパイルされて、その上でMonoが動いているということなのかな。多段変換だなぁ #unitej

emscriptenをつかうと、LLVM言語解析でコードを変換することができる。 #unitej pic.twitter.com/Z9mWkNWphk

emscriptenを使って、C/C++で実装されたUnity ランタイムをasm.jsにクロスコンパイルしているらしい #unitej

asm.js で JS サブセッ形式で静的な型付をし、JIT コンパイル時に最適化を効かせてネイティブコードにコンパイルする。asm.js 形式には Firefox のみ対応している #unitej

asm.jsについて。javascriptは型が不定なので最適なコードを出しにくいが、asm.jsではなんとか最適なコードを出力する。asm.jsが使えるブラウザはより高速な動作が期待できる。現在はFirefoxのみ。いずれ対応ブラウザが増えていく都思われる #unitej


C#/UnityScriptの変換はIL2CPPでC++にしてemsへ。  #unitej #room1

ユーザーコードのJavascriptへの変換はどうするか。IL2CPPを用意した。.NET bytecodeをC++にするもの。これで変換したのち、emscriptenでjavascriptへするという流れ。 #unitej

IL2CPP で .NET バイトコードを C++ コードに変換、それを Clang で LLVM に変換、それを emscripten で JavaScript に変換！ #unitej

UnityScript → .NET Byte Code→LLVM Byte Code→asm.js #unitej

Unity 5.0 ではビルドダイアログの Platform に Flash や NaCl はなくなって、WebGL が追加される #unitej

WebGL向けに出力されたJavascriptコード見てn88Basic時代の高速化を思い出すなど #unitej pic.twitter.com/ZksI6gRLQO

Unity5.0で、BuildTargetとしてGoogleNaclとFlashがDisconされた。  #unitej #room1

現状は Firefox が asm.js 効く分速い。JS には SIMD やマルチスレッド対応していないので他のプラットフォームより遅い。ネイティブと比較すると遅くて 50% くらいスピードが落ちる（逆にそれしか落ちないのか... #unitej

パフォーマンスはどうか。実際ケースバイケース。どのブラウザなのかもある。現在はasm.js対応のあるFirefoxが一番早い。SIMD、マルチスレッドがJavascriptは未対応なのでスキニングはかなり重いと感じる。WebPlayerに比べると50％程度かと。 #unitej

プラグインにも対応できる。javascriptのコードを書いておいて、実行時にコールできる。C++のコードをプロジェクトに入れておいて、それをコールすることもできる。なぜならコンバートされるから。 #unitej

プラグインはemscriptenで変換するのを考慮してC++で書いて、という感じ。 iOSとかのenvに対するプラグインをネイティブで書くのと一緒。  #unitej #room1

今後のロードマップ：Unity 5.0 では early-access、Unity 5.x ではフルサポートして early-access ラベルを外して、すべての主要なブラウザ上で動くようになる。ただ Web Player がなくなるわけではなく両方サポート  #unitej

UnityのWebGLサポートの仕組み。 C#ソース -(mcs)-> .NET bytecode  -(IL2CPP)-> C++ソース -(clang)-> LLVM bitcode -(emscripten w/ asm.js)-> Javascript  #unitej

WebPlayerはなくならない。WebGLと両面でいくが、いずれブラウザがプラグインを許可しなくなると思うので、その際には無くなる。 #unitej

プラグインとしてのUnityWebPlayerや、その他のプラグインはそもブラウザからブッ殺される予定で、とりあえずサポートは継続される。  #unitej  #room1

WebGL 2.0 になると OpenGL ES 3.0 サポートになる。するともっとリッチな表現が可能になる。SIMD / Multithreading はブラウザベンダで話し合われており、将来これらに対するソリューションが出てきて、ネイティブとのギャップが縮まる#unitej

WebGLは今後一般的になる。いろいろなブラウザで対応中。WebGL2。0は今後1年で出てくる。GLES3はより表現力を高める。SIMD、マルチスレッドについてはブラウザ各社が検討中だが方式が定まってない #unitej

こんなものが #unitej ： FirefoxでゲームパッドAPIを使うサンプル - 強火で進め d.hatena.ne.jp/nakamura001/20…


主婦「TransparentのReflectiveが…」 ゴロマンさん「なんでそんな言葉知っているんですかｗ！」 ( #unitej live at ustre.am/1bKAN)





Houdini Engine で作成したマップはUnityに持っていくことも、Mayaに持っていくことも出来る(Mayaはまだテスト版）。Win,Mac,Linuxで動く。本来はハリウッド映画VFK用。スマホ用VRもあるから試してみて！だそう #unitej

基本無料でサーバ作れるPhotonが５つのサービスに分裂。チャット機能に特化したり、ターン型対戦に特化したり、Unityに特化したり、またgheみたいにコード提供＆自社サーバ、といったことも可能に！ #unitej

AndtoidをワイヤレスモーションコントローラーにするときはSocket.setTcpNoDelay(true)は必須 #unitej



学べるとかより、2Dゲームを`構築`できるとか、3Dキャラクターをメカニムを使って`コントロール`できるという、行動を表す動詞を使った方がいい。メカニムの様な専門用語は文末に持ってくると、生徒を怖がらせない。らしいけど、日本語だと文末に持ってくるの難しいなw #unitej




ステキ RT @hecomi: Unity のプロファイラは他のプラットフォームと同じく使える。WebGL はプラグインのサポートもしていく。ある特定の関数を JS で書き、スクリプトから直接コールすることも出来る。 #unitej
