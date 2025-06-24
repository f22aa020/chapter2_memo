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

# 0528

### Flutter のバージョンが新しくなったことによる文法の非推奨や変更により、エラーが出てしまうことも。
### Key key → super.key
### FlatButton は非推奨になっており、代わりに TextButton を使用する必要がある
```ruby:qiita.rb
import 'package:flutter/material.dart'; 

// アプリのエントリーポイント（最初に実行される関数）
void main() {
  runApp(MyApp()); // MyApp ウィジェットをルートとして実行
}

StatelessWidget
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Generated App', // アプリのタイトル
      theme: ThemeData(
        primarySwatch: Colors.blue, // メインカラーの設定（マテリアルカラー）
        primaryColor: Color(0xFF2196f3), // アプリバーなどに使う色
        canvasColor: Color(0xFFfafafa), // 背景色
      ),
      home: MyHomePage(), // アプリ起動時に表示する画面
    );
  }
}

// 状態を持つウィジェット
class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key}); // キーを渡す

  @override
  _MyHomePageState createState() => _MyHomePageState(); // 状態クラスを作成
}

// 実際のUIと状態管理を行うクラス
class _MyHomePageState extends State<MyHomePage> {
  // 表示するメッセージ
  String _message = 'ok.';

  // じゃんけんの手の候補リスト
  final List<String> _janken = ['グー', 'チョキ', 'パー'];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar( // 画面上部のアプリバー
        title: Text('App Name'), // タイトル表示
      ),
      body: Center( // 画面中央に表示
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center, // 縦方向の中央寄せ
          children: [
            // メッセージ表示部分
            Padding(
              padding: EdgeInsets.all(20.0), // 余白を追加
              child: Text(
                _message, // 現在のメッセージを表示
                style: TextStyle(
                  fontSize: 32.0, // フォントサイズ
                  fontWeight: FontWeight.w400, // 太さ
                  fontFamily: "Roboto", // フォント
                ),
              ),
            ),
            // アイコン付きのテキストボタン
            TextButton(
              onPressed: buttonPressed, // ボタンが押されたときの処理
              child: Padding(
                padding: EdgeInsets.all(10.0), // アイコンに余白を追加
                child: Icon(
                  Icons.android, // Androidアイコンを表示
                  size: 50.0, // アイコンサイズ
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }

  // ボタンが押されたときに呼び出される関数
  void buttonPressed() {
    setState(() {
      // じゃんけんの手をシャッフルし、先頭の1つをメッセージとして設定
      _message = (_janken..shuffle()).first;
    });
  }
}


```

# 0603 (P131~)

```ruby:qiita.rb
import 'package:flutter/material.dart';

// アプリのエントリーポイント（
void main() {
  runApp(const MyApp()); // MyAppウィジェットを実行
}

// アプリ全体のウィジェット
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo', // アプリのタイトル
      theme: ThemeData(
        // テーマカラー
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
      ),
      // ホーム画面としてMyHomePageを設定
      home: const MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}


// ホーム画面のウィジェット
class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key, required this.title});

  final String title; // タイトル

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

// ホーム画面の状態を管理するクラス
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.'; // 表示するメッセージ（初期値）

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('App Name'), // アプリバーのタイトル
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.start, // 縦方向の配置（上寄せ）
          mainAxisSize: MainAxisSize.max, // 利用可能なスペースを最大限使用
          crossAxisAlignment: CrossAxisAlignment.stretch, // 横方向に広げる
          children: <Widget>[
            // メッセージを表示するテキスト
            Padding(
              padding: EdgeInsets.all(20.0),
              child: Text(
                _message,
                style: TextStyle(
                  fontSize: 32.0,
                  fontWeight: FontWeight.w400,
                  fontFamily: "Roboto",
                ),
              ),
            ),

            // 間隔をあけるための空白
            Padding(
              padding: EdgeInsets.all(10.0),
            ),

            // ボタンを表示
            Padding(
              padding: EdgeInsets.all(10.0),
              child: ElevatedButton(
                onPressed: buttonPressed, // ボタンが押されたときの処理
                child: Text(
                  "tap me!", // ボタンのラベル
                  style: TextStyle(
                    fontSize: 32.0,
                    color: const Color(0xff000000),
                    fontWeight: FontWeight.w400,
                    fontFamily: "Roboto",
                  ),
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }

  // ボタンが押されたときに呼ばれる関数
  void buttonPressed() {
    // ダイアログを表示
    showDialog(
      context: context,
      builder: (BuildContext context) => AlertDialog(
        title: Text("Hello!"), // ダイアログのタイトル
        content: Text("This is sample."), // ダイアログの本文
      ),
    );
  }
}

```



# 0604 (P140~)
### （何故か星が表示されない…→星の色のせい。ホワイトを変更する）

```ruby:qiita.rb
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

// アプリ全体のルートウィジェット
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        // アプリ全体のテーマカラー設定
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
      ),
      home: const MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}

// ホーム画面のStatefulWidget
class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key, required this.title});

  final String title;

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

// ホーム画面の状態（State）クラス
class _MyHomePageState extends State<MyHomePage> {
  // メッセージ表示用のテキスト
  static var _message = 'ok';
  // 星の表示（初期は全部「☆」）
  static var _stars = '☆☆☆☆☆';
  // 現在の星の数（0〜5）
  static var _star = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('My App'),

        // 左上の戻るボタン（白色）
        leading: BackButton(
          color: Colors.white,
        ),

        // 右上のアクションアイコン（2つ）
        actions: <Widget>[
          IconButton(
            icon: Icon(Icons.android),
            tooltip: 'add star...',
            onPressed: iconPressedA, // 星を増やす
          ),
          IconButton(
            icon: Icon(Icons.favorite),
            tooltip: 'subtract star...',
            onPressed: iconPressedB, // 星を減らす
          ),
        ],

        // AppBarの下に星を表示
        bottom: PreferredSize(
          preferredSize: const Size.fromHeight(30.0),
          child: Center(
            child: Text(
              _stars, // 現在の星の状態を表示
              style: TextStyle(
                fontSize: 22.0,
                color: Colors.white,
              ),
            ),
          ),
        ),
      ),

      // 中央にメッセージを表示
      body: Center(
        child: Text(
          _message,
          style: const TextStyle(
            fontSize: 28.0,
          ),
        ),
      ),
    );
  }

  // 「android」アイコンをタップしたときの処理
  void iconPressedA() {
    _message = 'tap "android".'; // メッセージ変更
    _star++; // 星を1つ増やす
    update(); // 状態更新
  }

  // 「favorite」アイコンをタップしたときの処理
  void iconPressedB() {
    _message = 'tap "favorite".'; // メッセージ変更
    _star--; // 星を1つ減らす
    update(); // 状態更新
  }

  // 星の数と表示を更新する関数
  void update() {
    // 星の数を0〜5の範囲に制限
    _star = _star < 0 ? 0 : _star > 5 ? 5 : _star;

    setState(() {
      // 「★★★★★☆☆☆☆☆」の中から該当部分だけを抽出
      // 例: _star = 3 の場合 → 5 - 3 = 2 から5文字 → 「★★★☆☆」
      _stars = '★★★★★☆☆☆☆☆'.substring(5 - _star, 5 - _star + 5);
      // メッセージに星の数を追加
      _message = _message + '[$_star]';
    });
  }
}


```
### class _MyHomePageStateからを変更

```ruby:qiita.rb
class _MyHomePageState extends State<MyHomePage> {
  // 表示するメッセージ
  static var _message = 'ok';

  // 現在選択されているBottomNavigationBarのインデックス（0〜2）
  static var _index = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      // 上部のアプリバー
      appBar: AppBar(
        title: Text('My App'), // タイトル文字
      ),

      // 画面中央にメッセージを表示
      body: Center(
        child: Text(
          _message, // 表示するテキスト
          style: const TextStyle(
            fontSize: 28.0, // 文字サイズ
          ),
        ),
      ),

      // 画面下部のナビゲーションバー
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: _index, // 現在選択されているタブ
        backgroundColor: Colors.lightBlueAccent, // 背景色

        // ナビゲーションバーに表示するアイテム（3つ）
        items: <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            label: 'Android', // ラベル名
            icon: Icon(Icons.android, color: Colors.black, size: 50), // アイコン
          ),
          BottomNavigationBarItem(
            label: 'Favorite',
            icon: Icon(Icons.favorite, color: Colors.red, size: 50),
          ),
          BottomNavigationBarItem(
            label: 'Home',
            icon: Icon(Icons.home, color: Colors.white, size: 50),
          ),
        ],

        // アイコンがタップされたときの処理
        onTap: tapBottomIcon,
      ),
    );
  }

  // ナビゲーションバーのアイコンがタップされたときに呼び出される関数
  void tapBottomIcon(int value) {
    // 各インデックスに対応する文字列リスト
    var items = ['Android', 'Heart', 'Home'];

    setState(() {
      _index = value; // タップされたアイコンのインデックスを保存
      _message = 'you tapped: "' + items[_index] + '".'; // メッセージを更新
    });
  }
}



```

# TODO アプリ
```ruby:qiita.rb
import 'package:flutter/material.dart';

void main() {
  runApp(const TodoApp()); // アプリの起動
}

// アプリ全体のウィジェット
class TodoApp extends StatelessWidget {
  const TodoApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'ToDo List',
      theme: ThemeData(
        primarySwatch: Colors.blue, // 青色テーマ
      ),
      home: const TodoHomePage(), // ホーム画面を指定
    );
  }
}

// ホーム画面（タスクリスト表示など）
class TodoHomePage extends StatefulWidget {
  const TodoHomePage({Key? key}) : super(key: key);

  @override
  State<TodoHomePage> createState() => _TodoHomePageState();
}

// ホーム画面の状態を管理するクラス
class _TodoHomePageState extends State<TodoHomePage> {
  final TextEditingController _controller = TextEditingController(); // テキスト入力コントローラー
  final List<TodoItem> _todoList = []; // タスクのリスト

  // タスクを追加する関数
  void _addTodo() {
    final text = _controller.text.trim(); // 入力値を取得
    if (text.isNotEmpty) {
      setState(() {
        _todoList.add(TodoItem(title: text)); // タスクを追加
        _controller.clear(); // 入力欄をクリア
      });
    }
  }

  // チェックボックスのON/OFF切り替え
  void _toggleComplete(int index) {
    setState(() {
      _todoList[index].isDone = !_todoList[index].isDone;
    });
  }

  // タスクを削除
  void _deleteTodo(int index) {
    setState(() {
      _todoList.removeAt(index);
    });
  }

  // UIのビルド
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('ToDo リスト'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          children: [
            // 入力フォームと追加ボタン
            Row(
              children: [
                Expanded(
                  child: TextField(
                    controller: _controller,
                    decoration: const InputDecoration(
                      hintText: '新しいタスクを入力',
                    ),
                  ),
                ),
                IconButton(
                  icon: const Icon(Icons.add),
                  onPressed: _addTodo, // タスク追加処理
                ),
              ],
            ),
            const SizedBox(height: 20),

            // タスクリスト表示
            Expanded(
              child: _todoList.isEmpty
                  ? const Center(child: Text('タスクがありません'))
                  : ListView.builder(
                      itemCount: _todoList.length,
                      itemBuilder: (context, index) {
                        final item = _todoList[index];
                        return ListTile(
                          leading: Checkbox(
                            value: item.isDone,
                            onChanged: (_) => _toggleComplete(index),
                          ),
                          title: Text(
                            item.title,
                            style: TextStyle(
                              decoration: item.isDone
                                  ? TextDecoration.lineThrough // 完了タスクは取り消し線
                                  : null,
                            ),
                          ),
                          trailing: IconButton(
                            icon: const Icon(Icons.delete),
                            onPressed: () => _deleteTodo(index), // タスク削除
                          ),
                        );
                      },
                    ),
            ),
          ],
        ),
      ),
    );
  }
}

// タスクのデータモデル
class TodoItem {
  String title;   // タスクの名前
  bool isDone;    // 完了状態（true: 完了）

  TodoItem({required this.title, this.isDone = false});
}

```


