# セットアップ(ubuntu)

*Ubuntu 20.04向けですが、一部を置き換えれば他のバージョンでも参考にできます。*
*v11とv12向けです。v10(m544等)は対象外です。*

## 最低限必要なもの

* nodejs
  * yarn (推奨)
* build-essential (パッケージ)
* redis
* postgresql

## 1. nodejsとyarnを入れる

### 1-1. nodejsのインストール

OSデフォルトのは古いので、NodeSourceが提供している物を使う。

```sh
# リポジトリを登録する
curl -fsSL https://deb.nodesource.com/setup_14.x | sudo -E bash -
# インストール
sudo apt-get install -y nodejs
```

### 1-2. yarnのインストール

なくてもよいが、misskeyはyarnを使って開発がされているためあったほうが良い。
**現状yarn2はサポートしていない**

```sh
# 鍵を登録
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
# リポジトリを登録
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
# 情報を更新してインストール
sudo apt update && sudo apt install yarn
```

## 2 redisとpostgresqlをインストール

最新のを使う場合は[2.1](#21-最新のredisとpostgresqlを使う場合)、Ubuntu標準のリポジトリのを使う場合は[2.2](#22-os標準ののredisとpostgresqlを使う場合)を参照すること。
組み合わせてpostgresqlだけ最新でredisはUbuntu標準のものを使うといった組み合わせもできる。

### 2.1 最新のredisとpostgresqlを使う場合

#### 2.1-1. redisのリポジトリ追加

```sh
# PPAにあるリポジトリを追加
sudo add-apt-repository ppa:chris-lea/redis-server
```

#### 2.1-2. postgresqlのリポジトリ追加

```sh
# リポジトリを登録
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

# 鍵を登録#postgresql-13
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```

#### 2.1-3. インストール

```sh
# 情報を更新してインストール
sudo apt update && sudo apt install redis postgresql-13
```

### 2.2 OS標準ののredisとpostgresqlを使う場合

```sh
# 情報を更新してインストール
sudo apt update && sudo apt install redis postgresql
```

これでMisskeyをビルドし、運用できる環境が完成したはずだ。

次: [Misskey本体の用意(まだできてない)](#)
