ansible_study
====

## What is this?

エンジニアリングスクール[RaiseTech](https://raise-tech.net/)のAWSフルコース第13回以降講座の課題：「Ansibleを使っての環境構築」を実施したものです。
- ruby(rbenv),nginx,node.jsのインストール、および必要コンポーネントのインストールを自動化しています。
- 本課題に関して詳細な手順書等のドキュメントはスクールより提供されておらず、AWS公式ドキュメントや検索サイトでヒットする情報を元に作成しています。
- 第14回講座で[Qiitaの記事](https://qiita.com/yuta-ushijima/items/decd8a5b6035fe76c010)が紹介されましたが、当該の記事は見ずに実施しています。

## 構成
- ディレクトリ構成

```
├── ansible.cfg
├── inventory
│   └── hosts
├── playbooks
│   └── playbook.yml
└── roles
    ├── common
    │   ├── defaults
    │   │   └── main.yml
    │   └── tasks
    │       └── main.yml
    ├── nginx
    │   ├── defaults
    │   │   └── main.yml
    │   └── tasks
    │       └── main.yml
    ├── nodejs
    │   ├── defaults
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    │   └── templates
    │       └── npm.sh.j2
    └── rbenv
        ├── defaults
        │   └── main.yml
        └── tasks
            └── main.yml
```

## 作成環境

- ansible:2.8.3
- ruby:2.6.3
- 対象ホスト:Amzxon Linux 2 (ami-0c3fd0f5d33134a76)+SSH公開鍵を追加したカスタムイメージを使用

## 導入

- リポジトリをgit cloneします。
- 対象ホストにSSHで接続できるように準備してください。
- hostsを参考にして接続先、公開鍵の保存場所やファイル名などを変更してください。
- ansible.cfgと同じディレクトリ内で、確認をします。
```
ansible-playbook -i inventory/hosts playbooks/playbook.yml --syntax-check
ansible-playbook -i inventory/hosts playbooks/playbook.yml --list-hosts
ansible-playbook -i inventory/hosts playbooks/playbook.yml --list-tasks
```

- 特にエラーが出なければ、実行します。
```
ansible-playbook -i inventory/hosts playbooks/playbook.yml
```


## 参考サイト

- [Best Practices — Ansible Documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html)
- [AnsibleのRole入門 ｜ DevelopersIO](https://dev.classmethod.jp/server-side/ansible/introduction_about_role/)
- [Playbookを再利用しやすくするRoleの基本と共有サービスAnsible Galaxyの使い方 (2/4)：Ansibleで始めるサーバ作業自動化入門（4） - ＠IT](https://www.atmarkit.co.jp/ait/articles/1610/05/news013_2.html)
- [nginx role(ansible galaxy)](https://galaxy.ansible.com/geerlingguy/nginx)
- [Ansible で rbenv をインストールする role を書いた](https://o296.com/e/Ansible%E3%81%A7rbenv%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E3%81%99%E3%82%8Brole%E3%82%92%E6%9B%B8%E3%81%84%E3%81%9F.html)

## 作成者

[@miima_17](https://twitter.com/miima_17)
