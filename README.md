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
cocoapodsを管理するためGemfileに以下を書きこむ
vimは`i`を一度押すと記入できるようになる。以下をかきこみ終わったら`:wq`を入れてエンターを押す
(wは書き込みqは終了です)
```
source "https://rubygems.org"

gem "cocoapods", "1.2.0"
```

9.gemfileを参照して、必要なgem(ここではcocoapods)を入れる
```
$ bundle install --path Vendor/Bundler
```

10.ios開発のためのライブラリ管理ツールpodの準備をする
まずはPodfileの作成
```
$ vi Podfile
```
Podfileの中身
```
# Uncomment the next line to define a global platform for your project
platform :ios, '9.0'

target 'wether_calendar' do
  # Comment the next line if you're not using Swift and don't want to use dynamic frameworks
  use_frameworks!
  pod 'FSCalendar', '~> 2.7.9'
  # Pods for wether_calendar

```

11.Podfileに登録したライブラリをおとしてくる
(bundlerでcocoapodを管理しているためpodのコマンドを使うときはbundle execを前につける必要がある)

```
$ bundle exec pod install
```
12.プロジェクトファイルを開く
```
open wether_calendar.xcworkspace
```

13.ビルドしてみる
多分できるはず

