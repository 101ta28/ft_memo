---
sidebar_position: 2
---

# Useful Settings

見た目を変えたり、機能を変えたり。

## Vimの設定

得られるもの

- 文字にハイライト

- スペースとタブが可視化

- 行番号の表示

```shell title=".vimrc"
echo -e "filetype plugin indent on\nset tabstop=4\nsyntax on\nset listchars=tab:>.,space:-,\nset list\nset number" >> ~/.vimrc
```

## Norminetteのインストール

リポジトリは[こちら](https://github.com/42School/norminette)

Pythonで書かれているので、pipでインストールする。

```bash
python3 -m pip install --user --upgrade pip setuptools

python3 -m pip install --user norminette==3.3.2
```

:::caution

<details>
	<summary>Ubuntu (WSL)でpipのエラーが出る時は...</summary>
	<div>
		<code>sudo apt install python3-pip</code> でpip自体をインストールする。
	</div>
</details>

:::

:::caution

<details>
	<summary>Macでpipのエラーが出る時は...</summary>
	<div>
		<code>python -m ensurepip --upgrade</code>でpipを導入する。
	</div>
</details>

:::

`norminette -v`を実行し、バージョンが表示されればOK

## おまけ

### 自前のPCから42のGitに接続する

*id_rsa*と*id_rsa.pub*の2つのファイルをダウンロードする。

ターミナル上で`mkdir ~/.ssh`を行い、ダウンロードしたファイルを .ssh ディレクトリに保存する。

:::note

既存の .ssh ディレクトリがあればそこに保存してもらって大丈夫です。

:::

ターミナルで .ssh ディレクトリに移動し`chmod 600 id_rsa id_rsa.pub`を実行し権限を変更する。

`chmod 700 ~/.ssh`でディレクトリの権限を変更する。

下記のコマンドを実行する。

```shell
ssh -T git@vogsphere-v2.42tokyo.jp
```

下記の文章が表示されたら**yes**を入力する

```shell
The authenticity of host 'vogsphere-v2.42tokyo.jp (XXX.XXX.XX.XXX)' can't be established.
ECDSA key fingerprint is なんか長いやつ Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

`Hi there, <42のユーザー名>! You've successfully authenticated with the key`が表示されればOK
