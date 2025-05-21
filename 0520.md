# 0520
```ruby:qiita.rb
//Flutterのマテリアルデザインライブラリをインポート
import 'package:flutter/material.dart';

//runApp()：指定したウィジェットをルートとしてアプリを起動します。
//MyApp()：自作のウィジェットを使用。

void main() {
  runApp(MyApp());
}

//MaterialApp
//Flutterアプリのルートを構築するためのウィジェット。
//title: アプリのタイトルを設定。
//Scaffold
//マテリアルデザインの基本的なレイアウト構造を提供。
//appBar: 上部にアプリバーを表示。

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Hell,Flutter!'),
        ),
        body : Text('Hell,Flutter World!',
        style: TextStyle(fontSize:32.0),
      ),
      ),
    );
  }
}
```


# 0521
```ruby:qiita.rb
// Flutterのマテリアルデザインライブラリをインポート
import 'package:flutter/material.dart';

// アプリのエントリーポイント（最初に実行されるmain関数）
void main() {
  runApp(const MyApp()); // アプリ全体をMyAppウィジェットで構築して起動
}

// アプリ全体を定義するStatelessWidget（不変のウィジェット）
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  // アプリで使用する定数のタイトルとメッセージ
  static const String title = 'Flutterサンプル';
  static const String message = 'サンプル・メッセージ';

  @override
  Widget build(BuildContext context) {
    // MaterialAppはアプリ全体の構造やテーマを設定するためのウィジェット
    return MaterialApp(
      title: 'Flutter Demo', // 内部的なアプリタイトル（主にデバッガ用）
      home: MyHomePage( // ホーム画面として表示するウィジェットを指定
        title: title,   // AppBarに表示するタイトルを渡す
        message: message, // Bodyに表示するメッセージを渡す
      ),
    );
  }
}

// 状態を持つウィジェット（StatefulWidget）を定義
// 状態（State）を変化させたい場合に使用する
class MyHomePage extends StatefulWidget {
  final String title;   // AppBarで使用するタイトル
  final String message; // Bodyに表示するメッセージ

  const MyHomePage({
    Key? key,
    required this.title,
    required this.message,
  }) : super(key: key);

  @override
  _MyHomePageState createState() => _MyHomePageState(); // 状態を管理するStateクラスを作成
}

// MyHomePageの状態を管理するクラス
class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    // Scaffoldは画面の基本的なレイアウト（AppBarやBodyなど）を提供する
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title), // 受け取ったタイトルをAppBarに表示
      ),
      body: Center(
        // 中央にテキストを配置
        child: Text(
          widget.message, // 受け取ったメッセージを表示
          style: const TextStyle(fontSize: 32.0), // フォントサイズを32に設定
        ),
      ),
    );
  }
}


```
```ruby:qiita.rb
// Flutterのマテリアルデザインライブラリをインポート
import 'package:flutter/material.dart';

// アプリのエントリーポイント（main関数）
void main() {
  runApp(const MyApp()); // アプリ全体をMyAppウィジェットで構築して起動
}

// StatelessWidget（状態を持たないウィジェット）でアプリ全体の構成を定義
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  // アプリのタイトルを定義
  final title = 'Flutterサンプル';

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo', 
      home: MyHomePage(
        title: this.title, // ホーム画面にタイトルを渡す
      ),
    );
  }
}

// 状態を持つホーム画面のウィジェット（StatefulWidget）を定義
class MyHomePage extends StatefulWidget {
  // タイトルを受け取るためのプロパティ
  const MyHomePage({required this.title}) : super();

  final String title; // AppBarに表示されるタイトル

  @override
  _MyHomePageState createState() => _MyHomePageState(); // 状態管理クラスを生成
}

// 実際のUIと状態を管理するクラス（State）
class _MyHomePageState extends State<MyHomePage> {
  // 表示されるメッセージの状態
  String _message = 'Hello!';

  // ボタンが押されたときに呼び出されるメソッド
  void _setMessage() {
    setState(() {
      _message = 'タップしました！'; 
    });
  }

  @override
  Widget build(BuildContext context) {
    // 画面全体のレイアウトをScaffoldで構築
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title), // 受け取ったタイトルをAppBarに表示
      ),
      body: Center(
        // 中央にメッセージを表示
        child: Text(
          _message, // 現在のメッセージを表示
          style: TextStyle(fontSize: 32.0), 
        ),
      ),
      // 右下に表示されるアクションボタン
      floatingActionButton: FloatingActionButton(
        onPressed: _setMessage, // ボタンが押されたときにメッセージを変更
        tooltip: 'set message.', // 長押しで表示される説明
        child: Icon(Icons.star), // ボタンに星アイコンを表示
      ),
    );
  }
}


```

