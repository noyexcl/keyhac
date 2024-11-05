# ビルド方法

VS2022でこのプロジェクトビルドしたら、何々足りないと言われるのでそれをポチポチ入れてたら出来た

ただし、それで出来るのは keyhac.exe だけであり、その他必要なファイルは makefile.py を実行する必要がある

makefile.py に必要なものは以下の通り

1. Python(3.8)(32bit)
2. Pillow(Pythonの画像処理するライブラリ)
3. Doxygen(ドキュメントを生成するツール)
4. pyautocore.pyd(*)
5. ckitcore.pyd(*)

Pythonは3.8.10(32bit)を使用し C:/Python38 以下にインストールする

そしてpipでPillowもインストールしておく

Doxygenはドキュメントに必要っぽいので、C:/Program Files/doxygen 以下にインストールした(makefile.py書き換えれば任意の場所で良い)

pyautocore.pyd は同作者のOS機能など低レベルの機能を扱うライブラリ pyauto のビルド成果物である。こちらもVS2022でポチポチしてたら普通にビルドできた

当プロジェクトでは面倒くさいのでリポジトリに直接放り込んであるから、わざわざビルドする必要はない

ckitはよく分からん。GUIとかウィンドウ操作、コマンド実行とかをやってるっぽい？
こっちもすでにビルド済み

基本的に、Pythonコードを編集し、C++の部分をいじるのでなければ

```python
python makefile.py
```

でビルドできるはず。成果物はdist以下にある
