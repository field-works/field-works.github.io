Hello World (5) ― テキスト属性 ―
==================================

主なテキスト属性を使ってみましょう。

単数行
------
text-align属性とvertical-align属性により，単数行テキストでの整列方法を指定します。

.. code-block:: javascript

    // hello5-1.json
    {
        "template": {"paper": "A4"},
        "context": {
            "hello": [
                {
                    "new": "Tx",
                    "rect": [100, 700, 400, 750],
                    "value": "左寄せ",
                    "text-align": "Left"
                },
                {
                    "new": "Tx",
                    "rect": [100, 600, 400, 650],
                    "value": "中央寄せ",
                    "text-align": "Center"
                },
                {
                    "new": "Tx",
                    "rect": [100, 500, 400, 550],
                    "value": "右寄せ",
                    "text-align": "Right"
                },
                {
                    "new": "Tx",
                    "rect": [100, 400, 400, 450],
                    "value": "均等割付",
                    "text-align": "Justify"
                },
                {
                    "new": "Tx",
                    "rect": [100, 300, 400, 350],
                    "value": "省略時左寄せ"
                }
            ]
        },
        "style": [
            {"hello.*": {"font-size": 18,
                         "border-width": 1}}
        ]
    }

.. figure:: img/実行結果5-1.png

    実行結果1

.. code-block:: javascript

    // hello5-2.json
    {
        "template": {"paper": "A4"},
        "context": {
            "hello": [
                {
                    "new": "Tx",
                    "rect": [100, 700, 400, 750],
                    "value": "垂直上寄せ",
                    "vertical-align": "Top"
                },
                {
                    "new": "Tx",
                    "rect": [100, 600, 400, 650],
                    "value": "垂直中央寄せ",
                    "vertical-align": "Middle"
                },
                {
                    "new": "Tx",
                    "rect": [100, 500, 400, 550],
                    "value": "垂直下寄せ",
                    "vertical-align": "Bottom"
                },
                {
                    "new": "Tx",
                    "rect": [100, 400, 400, 450],
                    "value": "省略時中央寄せ"
                },
                {
                    "new": "Tx",
                    "rect": [100, 300, 400, 350],
                    "value": "左上寄せ",
                    "text-align": "Left",
                    "vertical-align": "Top"
                }
            ]
        },
        "style": [
            {"hello.*": {"font-size": 18,
                         "text-align": "Center",
                         "border-width": 1}}
        ]
    }

.. figure:: img/実行結果5-2.png

    実行結果2

複数行
------
multiline属性にtrueを設定すると，複数行テキストとして表示します。
line-height属性により，改行幅を設定します。
改行幅はフォントサイズの倍率で指定しますので，フォントサイズが14pt，改行幅が1.5であれば，次の行は21pt下になります（行間の隙間が7ptになる）。

複数行モードでは，テキスト中に改行コードがあると，その位置で改行します。

.. code-block:: javascript

    // hello5-3.json
    {
        "template": {"paper": "A4"},
        "context": {
            "hello": [
                {
                    "new": "Tx",
                    "rect": [100, 600, 500, 750]
                },
                {
                    "new": "Tx",
                    "rect": [100, 400, 500, 550],
                    "text-align": "Center",
                    "line-height": 1.5
                }
            ]
        },
        "style": [
            {"hello.*": {
                "font-size": 14,
                "border-width": 1,
                "value": "「遊ぼう」っていうと 「遊ぼう」っていう。\n「馬鹿」ってい
                  うと 「馬鹿」っていう。\n「もう遊ばない」っていうと 「遊ばな
                  い」っていう。\n\nそうして、あとで 寂しくなって、\n「ごめんね」っ
                  ていうと 「ごめんね」っていう。\nこだまでしょうか、いいえ、誰で
                  も。",
                "multiline": true}
            }
        ]
    }

.. figure:: img/実行結果5-3.png

    実行結果3

行の長さがフィールドの幅を超える場合は，自動的に行を分割します。
 
行の分割の際には，日本語の禁則処理を行います。
さらに，複数行でtext-align属性が"Justify"に設定されると，行の右端がそろうように文字間スペースを調節します。

.. code-block:: javascript

    // hello5-4.json
    {
        "template": {"paper": "A4"},
        "context": {
            "hello": [
                {
                    "new": "Tx",
                    "rect": [50, 500, 560, 800]
                },
                {
                    "new": "Tx",
                    "rect": [50, 150, 560, 450],
                    "text-align": "Justify"
                }
            ]
        },
        "style": [
            {"hello.*": {"font-size": 15,
                         "border-width": 1,
                         "value": "作者はさっき、「下人が雨やみを待っていた」と書い
                           た。しかし、下人は雨がやんでも、格別どうしようと云う当て
                           はない。ふだんなら、勿論、主人の家へ帰る可き筈である。所
                           がその主人からは、四五日前に暇を出された。前にも書いたよ
                           うに、当時京都の町は一通りならず衰微していた。今この下人
                           が、永年、使われていた主人から、暇を出されたのも、実はこ
                           の衰微の小さな余波にほかならない。だから「下人が雨やみを
                           待っていた」と云うよりも「雨にふりこめられた下人が、行き
                           所がなくて、途方にくれていた」と云う方が、適当である。そ
                           の上、今日の空模様も少からず、この平安朝の下人の
                           Sentimentalismeに影響した。申の刻下りからふり出した雨
                           は、いまだに上るけしきがない。そこで、下人は、何をおいて
                           も差当り明日の暮しをどうにかしようとして——云わばどうに
                           もならない事を、どうにかしようとして、とりとめもない考え
                           をたどりながら、さっきから朱雀大路にふる雨の音を、聞くと
                           もなく聞いていたのである。",
                         "line-height": 1.5,
                         "multiline": true}}
        ]
    }

.. figure:: img/実行結果5-4.png

    実行結果4

英文の場合は，基本的に単語間スペースの位置で行を分割します。
 
text-align属性がtrueであれば，単語の終わりの位置で右端を揃えます。
さらに，hyphens属性を"Auto"に設定すると，ハイフネーション処理を行います。

.. code-block:: javascript

    // hello5-5.json
    {
        "template": {"paper": "A4"},
        "context": {
            "hello": [
                {
                    "new": "Tx",
                    "rect": [50, 500, 550, 800]
                },
                {
                    "new": "Tx",
                    "rect": [50, 150, 550, 450],
                    "text-align": "Justify",
                    "hyphens": "Auto"
                }
            ]
        },
        "style": [
            {"hello.*": {"font-size": 18,
                         "font": "/Times-Roman",
                         "border-width": 1,
                         "value": "Alice was beginning to get very tired of sitting
                           by her sister on the bank, and of having nothing to do:
                           once or twice she had peeped into the book her sister
                           was reading, but it had no pictures or conversations in
                           it, `and what is the use of a book,' thought Alice
                           `without pictures or conversation?'\n\nSo she was
                           considering in her own mind (as well as she could, for
                               the hot day made her feel very sleepy and stupid),
                         whether the pleasure of making a daisy-chain would be
                           worth the trouble of getting up and picking the daisies,
                         when suddenly a White Rabbit with pink eyes ran close by
                           her.",
                         "line-height": 1.5,
                         "multiline": true}}
        ]
    }

.. figure:: img/実行結果5-5.png

    実行結果5

