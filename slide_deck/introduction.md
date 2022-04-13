---
marp: true
theme: gaia
paginate: true
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
---

# Introduction to the <br>programming language <br>"Python" <br>in radio astronomy

- 2022-04-13 / Python Tutorials
- Authored by Akio Taniguchi  
  Presented by Kaoru Nishikawa

![bg right:30% 80% contain](https://pbs.twimg.com/media/EL-esF5XsAEXxlw?format=jpg&name=medium)

---

## Contents

- なぜ天文学で Python を学ぶのか
  - (電波) 天文学とプログラミング
  - プログラミング言語 Python
- Python を学ぶ上で知っておきたいこと
  - Python だけで全てを解決しないようにしよう
  - 公式の機能・ドキュメントを知る癖をつけよう
  - 他者への技術的な思いやりを持った開発をしよう
  - 「分からないこと」はどんどん質問をしよう

---

## Contents

- 本日の課題
  - 2次方程式を解く
  - 1年の日数を返す関数を作る

---

## なぜ天文学で Python を学ぶのか

<!--
_footer: https://speakerdeck.com/jakevdp/the-unexpected-effectiveness-of-python-in-science
-->

![bg blur 85%](https://files.speakerdeck.com/presentations/1083b290db884f2ab5d04eb98580be94/slide_51.jpg?8001969)

---

## (電波) 天文学とプログラミング

- データ解析
  - リダクション : 生データから画像・スペクトルデータを生成
  - 要約・可視化 : 観測データのプロット・統計量への要約など
  - シミュレーション : 理論モデルの生成・観測データとの比較
- 装置開発
  - 望遠鏡制御 : 装置間の通信制御・データ取得・観測計画立案
  - 性能評価 : 装置の仕様と実観測データの比較・考察

---

## プログラミング言語 Python

- 特徴
  - 高水準の汎用スクリプト言語
  - シンプルで習得しやすい文法とデータ構造
  - 豊富な標準ライブラリ (battery included)
  - 科学用途の豊富な外部ライブラリ
- 用途
  - 科学計算・機械学習・ウェブ開発・通信制御など
  - 天文学に限らずプログラム初学者が学ぶ言語の筆頭候補

---

<!--
_footer: https://qph.fs.quoracdn.net/main-qimg-e75e13d665984b797b2f8401f7e03c1d
-->

![bg contain](https://qph.fs.quoracdn.net/main-qimg-e75e13d665984b797b2f8401f7e03c1d)

---

## プログラミング言語 Python

```python
from pathlib import Path


def rename_duplicate(filepath: Path, i: int) -> Path:
    """Get file name with no duplicate.

    Args:
        filepath: Path to a file.
        i: Counter.

    """
    _path = path if i == 0 else path.parent / f"{path.stem}({i}){path.suffix}"
    if _path.exists():
        return rename_duplicate(path, i + 1)
    return _path
```

---

## プログラミング言語 Python

- 2022年4月時点での Python
  - 最新バージョン : [3.10](https://www.python.org/downloads/release/python-3104/) (2022年10月に [3.11がリリース予定](https://peps.python.org/pep-0664/))
  - Google Colaboratory では 3.7 が使われている
  - これから始めるなら最新バージョンを使いましょう
- 参考 : バージョン 2.x 系の Python
  - 3.x 系とは文法等が互換ではないことに注意
    - 例 : `3/2 -> 1` (2.x), `3/2 -> 1.5` (3.x)
  - 一部のソフトウェアは未だに 2.x を使っている

---

## プログラミング言語 Python

- 科学計算ライブラリ
  - [NumPy](https://numpy.org/), [xarray](https://docs.xarray.dev/), [pandas](https://pandas.pydata.org/) : 多次元配列・表データの処理
  - [SciPy](https://scipy.org/), [scikit-learn](https://scikit-learn.org/) : 科学計算ライブラリ
  - [Astropy](https://www.astropy.org/) : 天文計算ライブラリ
- 可視化ライブラリ
  - [Matplotlib](https://matplotlib.org/) : 1-2次元データプロット
- その他
  - [Jupyter notebook / lab](https://jupyter.org/) : ブラウザベースの Python 対話実行環境

---

<!--
_footer: https://speakerdeck.com/jakevdp/the-unexpected-effectiveness-of-python-in-science
-->

![bg 85%](https://files.speakerdeck.com/presentations/1083b290db884f2ab5d04eb98580be94/slide_51.jpg?8001969)

---

## Python を学ぶ上で知っておきたいこと

<!--
_footer: https://insights.stackoverflow.com/survey/2019
-->

![bg blur](https://cdn.sstatic.net/insights/Img/Survey/2019/tech_network-1.svg?v=017e35626eaf)

---

## "Python" だけで全てを解決しないように

- Python にも得意不得意がある
  - 実行速度はそこまで高速ではないことが多い → 外部ライブラリ
  - 非同期処理など、直感的でないことも
- 外部ライブラリが使えないか検討する
  - 例えば NumPy の配列計算は高速な科学演算に必須
- 他のプログラミング言語を検討する (やり過ぎない程度で)
  - 例えばウェブ関連の開発なら JavaScript など
  - データの入出力ならデータ記述言語 (HTML, JSON, TOML, ...)

---

## Python だけで全てを解決しないように

- シェルスクリプト (UNIX コマンド) の理解も大事
  - パイプライン : 簡潔なデータ連続処理
  - 正規表現 : 効率的な文字列検索
- 一般的なデータ構造を知っておく
  - オレオレデータ形式を作らないようにしよう
  - FITS (天文), netCDF : 多次元配列
  - JSON, YAML, TOML : データ記述言語
  - CSV : 表データ

---

<!--
_footer: https://insights.stackoverflow.com/survey/2019
-->

![bg](https://cdn.sstatic.net/insights/Img/Survey/2019/tech_network-1.svg?v=017e35626eaf)

---

## 公式の機能・ドキュメントを知る

- [標準ライブラリ](https://docs.python.org/ja/3/library/index.html) : これだけでかなりのことができる
  - 時刻計算・並列計算・OS操作など
  - 全部覚える必要はないが、機能を探す癖をつけておく
- [Python ドキュメント](https://docs.python.org/ja/3/)
  - 標準ライブラリのヘルプ (引数の意味など) を全て網羅
  - Python のインタープリタでは `help(関数名)` でも見られる
- 外部ライブラリドキュメント (ほぼ英語)
  - 例えば `astropy documentation` などで検索してみましょう

---

## 他者への技術的な思いやり

- Python らしい標準的な書き方 → この Tutorials で学びましょう
  - Python には [標準的な書き方の指針](https://pep8-ja.readthedocs.io/ja/latest/) がある
  - Pythonic な文法を使いこなす (例えばイテレータなど)
- 可読性の高いコードの書き方を理解する
  - コードを複雑にしない書き方 (例えば Guard Clause)
  - 変数の命名方法 (例えば `end` と `last` はどっちを使うべき？)
- ドキュメントを残す (例えば [neclib のドキュメント](https://nanten2.github.io/neclib))
- <span style="color: #F00;">**重要 : ここでいう「他者」には「数ヶ月後の自分」も含まれます**</span>

---

## 「分からないこと」は質問しよう

- 調べたら分かること
  - エラー (例外) の意味 (大抵は検索すればヒットする)
  - ライブラリの使い方 (大抵はドキュメントがある)
- 調べても分からないこと
  - ある目的に対するライブラリの使い所 (技術選定)
  - 専門知識 (天体物理学) を必要とするコード
- ただ、最初のうちはあまり気にせず質問した方がいいかも
  - M1以上は「○○が分からない」的な質問から脱却しよう

---

## 参考文献・書籍

- Python documentation
  - [Python 標準ライブラリ](https://docs.python.org/ja/3/library/index.html)
  - [Python コードのスタイルガイド](https://pep8-ja.readthedocs.io/ja/latest/)
- Python Books
  - [みんなの Python 第4版](https://www.amazon.co.jp/dp/479738946X/ref=cm_sw_em_r_mt_dp_U_PYpUDbJYW9JRW)
  - [入門 Python 3](https://www.amazon.co.jp/dp/4873117380/ref=cm_sw_em_r_mt_dp_U_SYpUDbSDGBN6D)
  - [科学技術計算のための Python 入門](https://www.amazon.co.jp/dp/4774183881/ref=cm_sw_r_tw_dp_U_x_k0TUEbVANHNQMj)

---

- Library References
  - [NumPy](https://numpy.org/), [xarray](https://docs.xarray.dev/), [pandas](https://pandas.pydata.org/) : 多次元配列・表データの処理
  - [SciPy](https://scipy.org/), [scikit-learn](https://scikit-learn.org/) : 科学計算ライブラリ
  - [Astropy](https://www.astropy.org/) : 天文計算ライブラリ
  - [Matplotlib](https://matplotlib.org/) : 1-2次元データプロット
- Other Books
  - [リーダブルコード](https://www.amazon.co.jp/dp/4873115655/ref=cm_sw_r_tw_dp_U_x_WATUEbR6S95N0)
  - [UNIX コマンドブック 第4版](https://www.amazon.co.jp/dp/4797372281/ref=cm_sw_em_r_mt_dp_U_V8pUDbKDTPHAY)
