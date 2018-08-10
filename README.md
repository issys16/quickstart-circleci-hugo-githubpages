
quickstart-circleci-hugo
======

CircleCI x Hugo x GitHub Pages の構成のブログを
簡単に始められるようにテンプレート化したリポジトリです。

devブランチへのプッシュを起因に、以下を実行します。
- HugoのBuild
- Build済みソースをmasterブランチへプッシュ

Usage
============

### Step.1
このリポジトリをフォークしてください。

### Step.2
フォークしたリポジトリにてGitHub Pagesのブランチ設定を行ってください。
- master/docs配下を参照するように設定。

### Step.3
CircleCI側でフォークしたリポジトリを監視するように設定してください。

### Step.4
デプロイキーをWrite権限ありのものに変更してください。
(デフォルトはRead権限のみのため`git push`が実行できないため): 

    SSHの鍵を生成する。
    $ ssh-keygen

    公開鍵をGitHub上の対象リポジトリ>Settings>Deploy keysに追加する。
    $ cat ~/.ssh/id_rsa.pub

    秘密鍵をCircleCI上の対象リポジトリ>Settings>SSH Permissionsに追加する。
    $ cat ~/.ssh/id_rsa

### Step.5
Hugo Themesから好きなテーマを選択しsubmoduleとして追加する
https://themes.gohugo.io/ : 

    $ git submodule add https://github.com/mtn/cocoa-eh-hugo-theme themes/cocoa-eh

### Step.6
テーマに合わせてconfig.tomlを書き換える: 

    $ cp themes/cocoa-eh-hugo-theme/exampleSite/config.toml .

### Step.7
.circleci/config.ymlの初期設定(自分のgit情報に書き換えてください)

・34行目: 

    $ git config --global user.email "XXXXXXX"

・36行目:

    $ git config --global user.name "XXXXXXX"

### Step.8
リモートリポジトリのdevブランチにプッシュする: 

    $ git add -A
    $ git commit -m 'XXXXX'
    $ git push origin dev
