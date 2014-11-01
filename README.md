これは何
---------------------

AnsibleのPlaybookをroleを使って書くためのテンプレートです。
踏み台を使った接続を簡単にするため、Ansibleのコマンドを実行する時にインベントリファイルごとに特定のssh_configファイルを指定して接続するラッパを同梱しています。

使い方
---------------------

### サーバを構築する

1. inventoriesディレクトリにインベントリファイルを格納する
2. 対象のインベントリファイルを使って構築対象サーバに接続する時に特定のssh_configを適用したい場合はインベントリファイルと同名のssh_configファイルをssh_configsディレクトリに格納する
3. `ansible`コマンドに代わりに`bin/ansible`、`ansible-playbook`コマンドの代わりに`bin/play`コマンドを使用する

```
# ansible代替
bin/ansible <inventory-name> <group-name> "<ansible options>"
# ansible-playbook代替
bin/play <inventory-name> <playbook-name> "<ansible options>"
```

### 新しいroleを作成する

```
bin/make_role <<role name>>
```

ディレクトリ構成
---------------------

|ディレクトリ|用途|
|------------|----|
|bin         |コマンド格納|
|inventories |[インベントリファイル](http://docs.ansible.com/intro_inventory.html)格納|
|library     |[独自モジュール](http://docs.ansible.com/developing_modules.html)格納|
|roles       |[role](http://docs.ansible.com/playbooks_roles.html)格納|
|ssh_configs |インベントリファイルと同名の[ssh_configファイル](http://www.openbsd.org/cgi-bin/man.cgi/OpenBSD-current/man5/ssh_config.5)格納
