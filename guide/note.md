# プロジェクトの構造

結構ややこしい構造のプロジェクトになっている

まず、実際のフック部分を行うのは、C++主体で書かれたライブラリ pyauto であり、それをPythonを使い、pydにビルドして、keyhacから呼び出せるようにしている

ckitはPythonの割合が高いがこれも同様にpydにビルドしている

そしてこれらをkeyhacのpythonコード群から使用して、アプリケーションを作り、最終的にexeにビルドしている

このプロジェクト自体がやっていることはそれほど多くのことでななさそう


# Keymap何してんの

pyautoがキーボードをフックしているので、そこに挟みたい処理を関数で渡しているっぽい

Keymap.enableHookで登録されている以下の関数がそれぞれのイベントのエントリーポイントになっているようだ

1. _hook_onKeyDown
2. _hook_onKeyUp
3. _hook_onMouseDown
4. _hook_onMouseUp
5. _hook_onMouseWheel
6. _hook_onMouseHorizontalWheel

これらの関数はbool値を返す
何かしら処理を行い、本来のキーの出力が不要になった場合、True を返し、イベントを乗っ取る
何も行う処理がなかったなど、本来のキーをそのまま出力してほしい時は False を返す

# Keydownが発生した時の取るべき処理のパターン

1. 何もされてないキー -> 何もせずただ出力する
2. 何かしらバインドされているキー -> そのアクションを実行し、本来のキーの出力は破棄する
3. 置き換えられているキー -> 置き換えられたキーを出力し、本来のキーの出力は破棄する
4. 修飾キー化されているキー -> 内部的に修飾キーリストに追加した後、本来のキーを出力する
