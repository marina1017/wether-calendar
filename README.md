# 必須
ruby 2.3.1
rbenvが必要です
Xcode9.2

# 自分の環境

```
$ brew --version
```
Homebrew 1.5.12

```
$ rbenv --version
```
rbenv 1.1.1


# 環境構築方法
１このリポジトリをクローンする
このファイルを入れたいディレクトリに移動してから下記コマンドを実行する

```
$ git@github.com:marina1017/wether-calendar.git
```

2.rbenvをインストール
複数バージョンを管理することができるrbenvを入れます。
```
$ brew install rbenv ruby-build
```
入ったことを確認したらrbenvがどのバージョンが入ったのか確認
```
rbenv --version
```

3.今回使うrubyの指定バージョンを入れる
```
$ rbenv install 2.3.1
```
一応入ってきたかチェックする(いまPC内で使えるrubyバージョン一覧が出てくる)
```
$ rbenv versions
```
こんな感じで出てきたらOK
```
system
* 2.3.1 (set by...........)
```

4.このリポジトリ内で利用するrubyのバージョンを設定する
```
$ rbenv local 2.3.1
```

5.リハッシュする
```
$ rbenv rehash
```

6.gemのバージョン管理をおこなうbundlerをいれる
（PCのグローバルにgemをいれるとバージョン管理ができなくなるためこのリポジトリ内にgemを入れるようにする）
```
gem install bundler
```

7.gemを管理するgemfileをつくる
```
$ bundle init
```
ここでコマンドを打った、ディレクトリにGemfileが作られる

8.Gemfileの中身を記入 Gemfileを開く
```
$ vi Gemfile
```
Gemfileに以下を書きこむ
```
source "https://rubygems.org"

gem "cocoapods", "1.2.0"
```

9.gemfileを参照して、必要なgem(ここではcocoapods)を入れる
```
bundle install --path Vendor/Bundler
```

10.プロジェクトファイルを開く
```
open wether_calendar.xcworkspace
```

11.ビルドしてみる
多分できるはず

