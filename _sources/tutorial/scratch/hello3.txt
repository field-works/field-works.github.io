Hello World (3) ― フィールド属性 ―
====================================

フィールドには，前回使用したフォント以外にも様々な表示属性が設定できます。

境界線
------
フィールドの境界線に関連する属性として，以下があります。

- border-width
- border-style
- border-dash
- border-width

0より大きい数値で境界線の太さを与えると，境界線が表示されます。
単位はポイント(pt)です。

.. code-block:: javascript

    // hello3-1.json
    {
        "template": {"paper": "A4"},
        "context": {
            "hello_1": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 700, 400, 750],
                "border-width": 1
            },
            "hello_2": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 600, 400, 650],
                "border-width": 2
            },
            "hello_3": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 500, 400, 550],
                "border-width": 3
            },
            "hello_4": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 400, 400, 450],
                "border-width": 4
            },
            "hello_5": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 300, 400, 350],
                "border-width": 5
            }
        }
    }

.. figure:: img/実行結果3-1.png

    実行結果1

border-style
^^^^^^^^^^^^
以下の境界線スタイルがあります。

- Solid
- Dashed
- Beveled
- Inset
- UnderlineStyle

.. code-block:: javascript

    // hello3-2.json
    {
        "template": {"paper": "A4"},
        "context": {
            "hello_1": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 700, 400, 750],
                "border-width": 3,
                "border-style": "Solid"
            },
            "hello_2": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 600, 400, 650],
                "border-width": 3,
                "border-style": "Dashed"
            },
            "hello_3": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 500, 400, 550],
                "border-width": 3,
                "border-style": "Beveled"
            },
            "hello_4": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 400, 400, 450],
                "border-width": 3,
                "border-style": "Inset"
            },
            "hello_5": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 300, 400, 350],
                "border-width": 3,
                "border-style": "UnderlineStyle"
            }
        }
    }

.. figure:: img/実行結果3-2.png

    実行結果2

border-dash
^^^^^^^^^^^
破線のパターンを指定します。
 
交互に現れる破線と隙間の間隔を1要素以上の数値リストとして指定します。
1要素の場合，破線と隙間の長さは同じになります。2要素以上の場合，破線1, 隙間1, 破線2, … の順にそれぞれの長さを指定します。
 
例えば，[3, 3, 15, 3]と指定すれば一点鎖線になります。

.. code-block:: javascript

    // hello3-3.json
    {
        "template": {"paper": "A4"},
        "context": {
            "hello_1": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 700, 400, 750],
                "border-width": 3,
                "border-style": "Dashed",
                "border-dash": [3]
            },
            "hello_2": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 600, 400, 650],
                "border-width": 3,
                "border-style": "Dashed",
                "border-dash": [6]
            },
            "hello_3": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 500, 400, 550],
                "border-width": 3,
                "border-style": "Dashed",
                "border-dash": [9]
            },
            "hello_4": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 400, 400, 450],
                "border-width": 3,
                "border-style": "Dashed",
                "border-dash": [3, 9]
            },
            "hello_5": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 300, 400, 350],
                "border-width": 3,
                "border-style": "Dashed",
                "border-dash": [3, 3, 15, 3]
            }
        }
    }

.. figure:: img/実行結果3-3.png

    実行結果3

色指定
------

色を指定する属性として以下の3種類があります。

- color
- border-color
- background-color
 
色指定は，システムで定義された Black, Gray, White, Red, Green, … などの16色の名前で指定するか，グレースケール・RGB・CMYKモデルの色成分を数値のリストで指定します。

.. code-block:: javascript

    // hello3-4.json
    {
        "template": {"paper": "A4"},
        "context": {
            "hello_1": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 700, 400, 750],
                "border-width": 3,
                "color": "Red"
            },
            "hello_2": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 600, 400, 650],
                "border-width": 3,
                "border-color": [0, 0, 255]
            },
            "hello_3": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 500, 400, 550],
                "border-width": 3,
                "background-color": [128]
            },
            "hello_4": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 400, 400, 450],
                "border-width": 3,
                "border-color": "Purple",
                "background-color": [192, 192, 192]
            },
            "hello_5": {
                "new": "Tx",
                "value": "Hello, World!",
                "rect": [100, 300, 400, 350],
                "border-width": 3,
                "color": [64, 128, 192],
                "border-color": "Blue",
                "background-color": [192, 192, 192]
            }
        }
    }

.. figure:: img/実行結果3-4.png

    実行結果4

