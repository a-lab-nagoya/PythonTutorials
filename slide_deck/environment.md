---
marp: true
theme: gaia
paginate: true
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
---

# Construction of Python environments on macOS

- Authored by Akio Taniguchi  
  Updated by Kaoru Nishikawa

![bg right:30% 80% contain](https://pbs.twimg.com/media/EL-esF5XsAEXxlw?format=png&name=medium)

<style>
.center { display: flex; justify-content: center; }
</style>

---

## Contents

1. 環境構築とは何か
2. Python 実行環境の構築
2. プログラミング環境の構築
3. 仮想環境の構築

---

## 用語の説明

| | |
| --- | --- |
| Python インタープリタ | Python の文法で書かれた指示を解釈し、実行するプログラム |
| スクリプト | Python の文法で指示を書いたテキストファイル |
| パッケージ / ライブラリ | ある目的のためのスクリプトを集めて配布されているもの (厳密には違うので注意) |
| pip | 外部パッケージをインストールするコマンド |
| パッケージ管理ツール | pip の機能を使いながらバージョン管理まで行うツール (Pipenv, Poetry など) |

---

## 環境構築とは何か

- 環境構築
    - とあるプロジェクトに必要なライブラリ・Python インタープリタを独立にインストールすること
    - エディタ・linter (構文チェッカー)・formatter (自動整形) などプログラミングを支援する環境を整えること
- Python の環境構築
    - Python インタープリタ・標準ライブラリ → Homebrew を使う
    - 外部ライブラリ → pip またはパッケージ管理ツールを使う

---

## Python を起動してみる

まず Python がインストールされているか確認する

```shell
$ which python3
```

- 何も表示されなかった場合、`$ brew install python3`

<div class="center">

| | |
| --- | --- |
| Python を起動する | `$ python3` |
| Python を終了する | `>>> quit()` |

</div>

---

## 仮想環境の構築

バージョン管理ツール Poetry をインストールする

```shell
$ curl -sSL https://install.python-poetry.org | python3 -
$ poetry config virtualenvs.in-project true
```

作業を行うためのディレクトリを作り、仮想環境を作る

```shell
$ mkdir MyProject && cd MyProject
$ poetry init
```

いくつか設定を聞かれるが、後から変更できるため適当でも良い

---

## 仮想環境の使用

<div class="center">

| | |
| --- | --- |
| 仮想環境に入る | `$ poetry shell` |
| 仮想環境から出る | `$ exit` |
| 外部パッケージを追加する | `$ poetry add numpy` |
| 外部パッケージを削除する | `$ poetry remove numpy` |
| 外部パッケージを全てアップデートする | `$ poetry update` |
| 既存の poetry.lock ファイルを読み込む | `$ poetry install` |

</div>

---

## バージョンの異なる Python を使う

バージョンの異なる Python を使うために pyenv をインストールする

```shell
$ brew install pyenv
$ echo '# pyenv\nexport PYENV_ROOT=$HOME/.pyenv' >> ~/.zprofile
$ echo 'export PATH=$PYENV_ROOT/bin:$PATH' >> ~/.zprofile
$ echo 'eval "$(pyenv init --path)"' >> ~/.zprofile
```

Python 3.8.12 をインストールし、`python` コマンドに紐づける

```shell
$ pyenv install 3.8.12
$ pyenv global 3.8.12
```

---

## プログラミング環境の構築

<style scoped>
span {
    font-family: LucidaGrande, Osaka, AppleGothic, monospace;
    background-color: #FFF5AF;
    border-radius: 3px;
    padding: 3px;
}
.nested { list-style-type: circle; }
</style>

おすすめのツール・設定

- [Visual Studio Code](https://code.visualstudio.com/)
    - (拡張機能：<span>&#8984;&#8679;X</span>)
    - Python
    - Pylance
    - Jupyter
    - Code Spell Checker
    - Todo Tree

<div style="position: absolute; left: 42%; top: 39%;">

<ul class="nested">
<li>(設定：<span>&#8984;,</span>)</li>
<li>Editor: Format On Save <span>&#9745;</span></li>
<li>Python > Formatting: Provider <span>black</span></li>
<li>Python > Linting: Flake8 Enabled <span>&#9745;</span></li>
</ul>
</div>
