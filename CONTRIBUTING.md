# ビルド方法

VS2022でこのプロジェクトビルドしたら、何々足りないと言われるのでそれをポチポチ入れてたら出来た

ただし、それで出来るのは keyhac.exe だけであり、その他必要なファイルは makefile.py を実行する必要がある

makefile.py に必要なものは以下の通り

1. Python(3.8)(32bit)
2. Pillow (Pythonの画像処理するライブラリ)
3. Doxygen (ドキュメントを生成するツール)
4. pyautocore.pyd (キーボードフックなどを行う低レベルのライブラリ)
5. ckitcore.pyd (ウィンドウ操作などを行うライブラリ)

Pythonは3.8.10(32bit)を使用し C:/Python38 以下にインストールする

そしてpipでPillowもインストールしておく

Doxygenはドキュメントに必要っぽいので、C:/Program Files/doxygen 以下にインストールした(makefile.py書き換えれば任意の場所で良い)

pyautocore.pyd は同作者のOS機能など低レベルの機能を扱うライブラリ [pyauto](https://github.com/crftwr/pyauto) のビルド成果物である。こちらもVS2022でポチポチしてたら普通にビルドできた

当プロジェクトでは面倒くさいのでリポジトリに直接放り込んであるから、わざわざビルドする必要はない

[ckit](https://github.com/crftwr/ckit)はよく分からん。GUIとかウィンドウ操作、コマンド実行とかをやってるっぽい？
こっちもすでにビルド済みで直接リポジトリに入れてある (ckitcore.pyd)

基本的に、Pythonコードを編集し、C++の部分をいじるのでなければ

```python
python makefile.py
```

でビルドできるはず。成果物はdist以下にある
