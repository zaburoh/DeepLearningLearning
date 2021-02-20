# ゼロから作るDeepLearning

# 仮想環境

## 構築

```bash
$ python -m venv .
```

## 開始

```bash
$ source bin/activate
(DeepLearning) $
```

## 終了

```bash
(DeepLearning)$ deactivate
```

## libraries

- numpy
- matplotlib

### 一覧

```bash
(DeepLearning) $ pip list
Package       Version
------------- -------
numpy         1.20.1 
pip           18.1   
pkg-resources 0.0.0  
setuptools    40.8.0 
```
# 用語
| 用語 | 意味 | 例 |
| --- | --- | --- |
| 要素ごと | 英語で`element-wise`という | 「要素ごとの積」= `element-wise product` |
| スカラ | 単一の数値 | `2.0` |
| ブロードキャスト | Numpy配列の各要素とスカラ値で計算すること | `np.array([1.0, 2.0, 3.0]) / 2.0` |
| {配列}.shape | 行列の形状 | `(2, 2)` |
| {配列}.dtype | 行列の要素データ型 | `dtype('int32')` |
| ベクトル | 1次元配列 | `[1.0, 2.0, 3.0]` |
| 行列 | 2次元配列 | `[[1.0, 2.0], [3.0, 4.0]]` |
| テンソル、多次元配列 | ベクトルや行列を一般化したもの<br />または、3次元以上の配列のこと | - |

# NumPy
## ブロードキャスト
以下のような処理をした場合、10というスカラ値が2x2の要素に拡大されて演算が行われること。

```python
>>> A = np.array([[1, 2], [3, 4] ])
>>> A * 10
array([[10, 20],
       [30, 40]])
# 内部的には以下のように10という値が2x2の要素に拡大されている
>>> np.array([[1, 2], [3, 4]]) * np.array([[10, 10], [10, 10]])

# 2x2の要素を持つ配列と2x1の要素を持つ配列を計算した場合
>>> B = np.array([10, 20])
>>> A * B
array([[10, 40],
       [30, 80]])
# 内部的には以下のように[10, 20]という値が2x2の要素に拡大されている
>>> np.array([[1, 2], [3, 4]]) * np.array([[10, 20], [10, 20]])
```

## flatten()
多次元配列を１次元の配列へ変換する

```python
>>> X = np.array([[51, 55], [14, 19], [0, 4]])
>>> print(X)
[[51 55]
 [14 19]
 [ 0  4]]
>>> X = X.flatten()
>>> print(X)
[51 55 14 19  0  4]
```

## テンソル（多次元配列）から`15`以上の値を抽出する

```python
# 単純に'numpy.ndarray'に対して比較演算を行うと各要素の値の審議値が出力される　
>>> X > 15
array([ True,  True, False,  True, False, False])

# 添え字部分に比較演算を与えると条件を満たした値のみ抽出することができる
>>> X[X>15]
array([51, 55, 19])
```

## 補足
`NumPy`は主な処理については`C++`で実装されているため、パフォーマンスを損なうことなく計算ができるらしい。

# Matplotlib

## インストール

```bash
$ pip install matplotlib
# ~省略~
$ pip list
Package         Version
--------------- -------
cycler          0.10.0 <new>
kiwisolver      1.3.1  <new>
matplotlib      3.3.4  <new>
numpy           1.20.1 <numpy>
Pillow          8.1.0  <new>
pip             18.1   <default>
pkg-resources   0.0.0  <venv>
pyparsing       2.4.7  <new>
python-dateutil 2.8.1  <new>
setuptools      40.8.0 <default>
six             1.15.0 <new>
```

## グラフの描画

```python
>>> import matplotlib.pyplot as plt
Matplotlib is building the font cache; this may take a moment.
>>> x = np.arange(0, 6, 0.1)
>>> y = np.sin(x)
>>> plt.plot(x, y)
[<matplotlib.lines.Line2D object at 0xb375ac90>]
>>> plt.show()
```