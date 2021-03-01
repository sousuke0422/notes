# OSのアップグレードをするときの注意

glibcのロケールの参照順変更でデーターベースのインデックスが壊れるので注意。
なお、CやPOSIXロケールを使ってる場合は影響しないらしい。

コマンドを使う場合は、`pg_upgrade`や`pg_basebackup`ではなく`pg_dump`を用いる必要がある。
`pg_upgrade`や`pg_basebackup`だとインデックス情報も一緒に出力するらしい。

## 参考情報

* <https://blog.noellabo.jp/entry/2020/11/08/145740>
  * Mastodon向けの記事だけど、tootctlを使った解決ができないだけでだいたい同じ。

* <https://wiki.postgresql.org/wiki/Locale_data_changes>
  * どのバージョンのOSが危ないか書いてある。
