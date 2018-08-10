
quickstart-circleci-hugo
======

CircleCI x Hugo x GitHub Pages の構成のブログを
簡単に始められるようにテンプレート化したリポジトリです。

devブランチへのプッシュをトリガーとして、以下を実行します。
- HugoのBuild
- Build済みソースをmasterブランチへプッシュ

Usage
============

### Step.1
このリポジトリをフォークし、devブランチを`git clone`してください。

### Step.2
フォークしたリポジトリにてGitHub Pagesのブランチ設定を行ってください。 
※masterブランチのdocs配下を参照するように設定。

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
リモートリポジトリのdevブランチにプッシュする: 

    $ git add -A
    $ git commit -m 'XXXXX'
    $ git push origin dev

### Fin.
以上の操作でCircleCIが実行され、GitHub Pagesに反映されます。
