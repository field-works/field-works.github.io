インストールに関する質問
========================

.. contents:: 質問一覧
   :local:

PythonのDistributeのインストールに失敗します
--------------------------------------------
 
Pythonをソースからビルドした場合，ビルド時の環境によってはzlibモジュールが組み込まれないことがあるようです。
その場合には，以下のようなエラーメッセージが出力されます。

::

    File "/usr/local/lib/python2.7/zipfile.py", line 651, in __init__
      "Compression requires the (missing) zlib module"
    RuntimeError: Compression requires the (missing) zlib module

以下に示す方法で，Pythonをインストールし直してください。
 
(1) zlibのヘッダファイルとライブラリをインストールする。

CentOSの場合，“zlib-devel”というパッケージ名で導入できます（Debian系では“zlib1g-dev“）。

::

    # yum install zlib-devel
 
(2) Pythonを再ビルドする。

::

    # ./configure
    # make
    # make install
 
この方法で解決しない場合は，例えばCentOS 5.5 に Python 2.6.6 をインストール 等を参考にして，以下の方法を試みてください。

(3) configure時に共有ライブラリを有効にする。

(4) Modules/Setupを修正して，zlibモジュールを有効にする。

初期設定ファイルがありません
----------------------------

初期設定ファイルはインストーラにより作成されませんので，テキストエディタ等を使って手動で作成してください。

Linux版のインストール時にlibcurl関連のエラーが発生します
--------------------------------------------------------

Field Reportsはlibcurlに依存しています。
libcurlパッケージがインストールされていないと，インストール時に下記のようなエラーが出力されます。

::

    $ sudo rpm -ivh reports-1.4-3.x86_64.rpm
    エラー: Failed dependencies:
        libcurl.so.4()(64bit) is needed by reports-1.4-3.x86_64

ご使用中のLinuxディストリビューションで利用できるパッケージ管理ツールを使ってlibcurlをインストールしてください。
 
CentOSでの実行例::

    $ sudo yum install curl-devel
 
自前でlibcurlをインストールした場合には，rpmコマンドに“--nodeps”オプションを付けて実行してください。

::

    $ sudo rpm -ivh --nodeps reports-x.x-x.xxxx.rpm

rpmコマンドでバージョンアップできません
----------------------------------------

旧バージョンのField Reportsをアンインストールしてから新バージョンをインストールしてください。

::

    $ sudo rpm -e reports

Python言語Bridgeのインポートに失敗します
----------------------------------------

field.reportsライブラリのインポート時に次のような例外が発生することがあります。

::

    >>> import field.reports
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    ImportError: /usr/lib/python2.6/site-packages/field.reports-1.5-py2.6-linux-x86_64.egg/field/reports.so: undefined symbol: PyUnicodeUCS2_AsUTF8String

そのような場合には，Python言語Bridgeをソースからビルドしてインストールしなおしてください。

::

    $ tar xvzf field.reports-x.x.tar.gz
    $ cd field.reports-x.x
    $ sudo python setup.py install

ライセンスキーが認識されません
------------------------------

発行されたシリアル番号とライセンスキーを初期設定ファイルに登録しても生成されるPDFから(TRIAL)の赤文字が消えない場合には，以下の確認を行ってください。

(1) reportsコマンドでは(TRIAL)の文字が消える場合

コンソールからreportsコマンドを実行したときは(TRIAL)の文字が消えるがPHP等から実行した時には消えない場合には， 初期設定ファイルのアクセス権限をご確認ください。
PHPはApacheなどのWebサーバのプロセスから実行されます。
Webサーバの実行ユーザ（apache, http, wwwなど）から初期設定ファイルが見えない設定になっていないか確認してください。

::

    $ ls -l /etc/reports.conf

読み出しの実行権限が不足しているようでしたら， chmodでアクセス権を追加するか， chownでオーナーを変更するなどしてアクセス権限を与えてください。

::

    $ sudo chmod a+r /etc/reports.conf

(2) reportsコマンドでも(TRIAL)の文字が消えない場合

以下のような原因が考えられます。

- ライセンスキーの発行ミス
- メール配信過程での文字化け
- ライセンスキーを初期設定ファイルへコピーする際の一分文字の欠損

いすれにしてもサポート窓口までお問い合わせください。

