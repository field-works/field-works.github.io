Hello World (4) ― スタイル指定 ―
==================================

これまでは，個々のフィールドに対して属性を指定してきましたが，フィールド数が多くなってくるとレンダリング・パラメータの作成や修正がたいへんになってきます。「スタイル指定」を使って，作業を効率化しましょう。

フィールドの階層化
------------------
スタイル指定を効率的に行うためには，フィールドを階層化する必要があります。
 
PDFでは，F.a, F.b のようにピリオドで区切ったフィールド名を付けると，Fを親，aとbを子とする親子関係があると認識されます。
これは単なる命名習慣ではなく，PDFの中では実際にツリー状のデータ構造が組み立てられます。
 
一方，Adobe AcrobatでPDFにフィールドを配置する際に「復数のフィールドを配置…」でテーブル状にフィールドを並べると，F.0, F.1, … のように0始まりの数字のフィールド名が付けられます。
 
Field Reports では，これらPDFやAcrobatの性質を利用して，スタイル指定を行います。

レンダリング・パラメータの修正
------------------------------
スタイル指定を行う準備として，まずは前回作成した“hello3-2.json”を階層構造を持たせた形に修正します。
Field Reports では，0, 1, 2, … の並びをリストに対応付けます。

.. code-block:: javascript

    // hello4-1.json
    {
        "template": {"paper": "A4"},
        "context": {
            "hello": [
                {
                    "new": "Tx",
                    "value": "Hello, world!",
                    "rect": [100, 700, 400, 750],
                    "border-width": 3,
                    "border-style": "Solid"
                },
                {
                    "new": "Tx",
                    "value": "Hello, world!",
                    "rect": [100, 600, 400, 650],
                    "border-width": 3,
                    "border-style": "Dashed"
                },
                {
                    "new": "Tx",
                    "value": "Hello, world!",
                    "rect": [100, 500, 400, 550],
                    "border-width": 3,
                    "border-style": "Beveled"
                },
                {
                    "new": "Tx",
                    "value": "Hello, world!",
                    "rect": [100, 400, 400, 450],
                    "border-width": 3,
                    "border-style": "Inset"
                },
                {
                    "new": "Tx",
                    "value": "Hello, World!",
                    "rect": [100, 300, 400, 350],
                    "border-width": 3,
                    "border-style": "UnderlineStyle"
                }
            ]
        }
    }

スタイル要素の追加
------------------
次に，スタイル要素を追加します。
 
value, border-width が共通の値だったので，スタイル要素にまとめました。ただし，newはスタイル要素として記述できないので残しています。
 
ここで，"style"キーワードと対になる値のデータ型が辞書ではなくリストであることに注意してください。スタイルの適用順序が重要になる場面に備えて，順序が保存できるリストを使用しているためです。

.. code-block:: javascript

    // hello4-2.json
    {
        "template": {"paper": "A4"},
        "context": {
            "hello": [
                {
                    "new": "Tx",
                    "rect": [100, 700, 400, 750],
                    "border-style": "Solid"
                },
                {
                    "new": "Tx",
                    "rect": [100, 600, 400, 650],
                    "border-style": "Dashed"
                },
                {
                    "new": "Tx",
                    "rect": [100, 500, 400, 550],
                    "border-style": "Beveled"
                },
                {
                    "new": "Tx",
                    "rect": [100, 400, 400, 450],
                    "border-style": "Inset"
                },
                {
                    "new": "Tx",
                    "rect": [100, 300, 400, 350],
                    "border-style": "UnderlineStyle"
                }
            ]
        },
        "style": [
            {"hello.*": {"value": "Hello, world!", "border-width": 3}}
        ]
    }

セレクタ文字列
--------------
"hello.*"の部分を「セレクタ文字列」と呼び，スタイルを適用する範囲を規定します。
 
"*"は，任意の部分フィールド名ひとつにマッチします。
 
数値の範囲を規定するためのセレクタ文字列もあり，フィールドがテーブル状に並んでいる場面で威力を発揮します。
例えば，"[3:]"であれば3行目または3列目以降(3, 4, 5, ...)，"[1::2]"であれば奇数行または列(1, 2, 3, ...)に選択的にスタイルを適用することができます。

