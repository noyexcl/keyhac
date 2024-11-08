# このフォークについて

## バグ修正

本家 keyhac1.82 で発生する修飾キーのワンショットイベントが、タイピング速度によってたびたび不発になるバグを修正

## 追加の機能

### ホットキーによるフックの一時停止/再開

configファイル内で以下のように、仮想キーコードもしくは文字列で設定する

両方同じキーを設定しても良い

```python
keymap.suspendKey = 131  # Eject key を表すキーコード
keymap.resumeKey = "C-End"
```

### レイヤー機能

メインとは別にキーマップを作り、コマンドを実行することで、指定したキーマップに持続的に変更できる機能

レイヤーはキーマップの定義時に引数で指定し、コマンドは `keymap.SwitchLayerCommand` を使う

```python
main_keymap = keymap.defineWindowKeymap()          # レイヤーを指定しなかった場合、layer=0 になる
sub_keymap = keymap.defineWindowKeymap(layer=1)    # 定義時にレイヤーを指定

main_keymap["A-1"] = keymap.SwitchLayerCommand(1)  # レイヤーが1に設定されたキーマップに変更
sub_keymap["A-0"] = keymap.SwitchLayerCommand(0)   # レイヤーが0に設定されたキーマップに変更
```
### 使えるFnキーをF24まで拡張

```python
main_keymap["A-caret"] = "F24"
```
