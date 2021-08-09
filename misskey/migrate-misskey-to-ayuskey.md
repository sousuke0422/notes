# misskeyからayuskeyに移行する

## 注意

### 管理者向け
* **misskey v12からayuskey 5.xへの以降は対応していません**
* 一部の設定は初期化されます。
* 一部の設定は値が変更され、再設定が必要な場合があります。
* postgresに依存するノート検索を使用する場合、node 15以降が必須です。
### 利用者向け
* misskey v12式のMFMに対応していますが、mfm.jsが採用される以前の仕様です。 
* Safari(webkit)、iOSは現状考慮していません。必要があればissueを建ててください。程度にもよりますが、できる限り対応します。

## 手順
※問題は起きないはずですがバックアップをおすすめします。

### 1.リーモートをいじる
※gitが必要ですが、入っているはずなのでインストールは省きます。

```sh
git remote remove origin

git remote add origin https://github.com/TeamOrangeServer/misskey.git
```

### 2.ブランチを切り替える。
```sh
git fetch origin

git checkout v11-lts
```

### 3.日頃のバージョンアップと同じ手順
ここまで来れば後はかんたんです。

```sh
git pull

yarn install

NODE_ENV=production yarn build

yarn migrate
```

あとはmisskeyを再起動するだけです。
お疲れさまでした。
