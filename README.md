spindle/lib-template
========================

Composerでライブラリを作るときのオレオレテンプレートです。
CC0-1.0(権利放棄)なので、コピペしても特に連絡やクレジット表示は不要です。

## install

```sh
$ composer create-project spindle/lib-template path/to/project-dir
```

or

```sh
$ git clone git://github.com/spindle/spindle-lib-template.git path/to/project-dir
$ cd path/to/project-dir
$ rm -rf .git
$ composer install
```

プロジェクトを作り終わったら、gulpを追加。

```sh
$ sudo yum install nodejs npm
$ sudo npm install -g gulp
$ npm install
```

gitattributesは必要に応じてgitに追加してください。github.comで生成されるzipファイルの中身をカスタマイズできます。

```sh
$ mv gitattributes .gitattributes
```

パッケージ名を決めて、ファイルを編集しておいてください。

```sh
$ vim composer.json
$ vim README.md
```

phpunit.xml.distをphpunit.xmlにコピーし、HTMLのカバレッジレポートが出力されるよう設定を変更しておきます。
また、cloverの出力は(ローカル環境では)不要なので、削除しておきます。

## development

### ユニットテスト

```sh
$ gulp test
```

PHPUnitが起動し、tests/配下のすべてのテストケースを実行します。

### インスペクション

```sh
$ gulp inspect
```

`PHP_Depend`および`ApiGen`が起動し、builds/配下へレポートを出力します。
src配下のソースコードについて、APIドキュメントを作成し、コードメトリクスを計測します。


### ファイル変更監視 & 自動テスト

```sh
$ gulp server
```

src/およびtests/配下のファイル書き込みを監視し、何か変動があれば自動的にPHPUnitを実行します。
また、 http://localhost:9000/ でWebサーバーを立ち上げます。
ここにアクセスすると、生成されたドキュメントやカバレッジレポートを読むことができます。
ファイル書き込みと連動しており、変化があれば自動的にレポートはリロードされます。(livereload)

## Continuos Integration & Inspection

### travis-ci

### scrutinizer-ci

