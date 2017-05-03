# コントリビュートの方法

## 行動規定
フルテキストはこちら（これはFacebookにおけるコンダクト）
https://code.facebook.com/pages/876921332402685/open-source-code-of-conduct

何が良て何がダメなのかはここから紐解く。

## Branch Organization
マスターブランチがメインブランチ。テストは常に通るようにしておくこと。
ただし、行動を早くするためににApiが互換性がないかもしれない状態になっていることもある。
なので、latest stable varsionにしておくことがおすすめ。

## Semantic versioning

ReactではSemantic versioningを採用している。

全てのPRにはタグをつけている。


## Bugs
### New Issues
issue管理にはgithub issueを使用している。
新しく追加するときにはすでに登録されていないか注意指定欲しい

### Rporting New Issues
できるだけ、テストケースを追加しないでバグを修正するのがとても良い方法。
https://jsfiddle.net/84v837e9/
こちらがstarting pointとしてオススメ

### Security Bugs
FBはbounty program(バグ報酬制度)をセキュリティバグにたいして適用している。ただし、これについてはpublicなissueとしてはあげないで欲しい



## Your First Pull Request

簡単なissueは　`Difficulty: beginner` というタグがつけられている。
これは初めてコントリビュートするのには向いている。

issueを治すことをきめたら、コメントを確認して欲しい。すでに誰かそれを治す作業をしているかもしれない。
もし、誰も作業していないのならば、「治すよー！」という旨を伝えるコメントを残して欲しい。そうすれば、無駄がなくなる。

誰かが、問題定義して２週間以上フォローアップしていない場合は引き継ぐのがいいが、コメントは残して欲しい。

## Sending a pull request
コアチームはPRを見ている。
コアチームは、PRをレビューして、マージする。APIの変更についてはFBでの社内利用のための修正が必要な場合があるので少し遅れるかもしれない。全てのプロセスを通じて最良の香とは行うつもり。

### Before submitting a pull requeset

1. masterからフォークする
2. コードを書き加えたらテストを追加して！
3. APIを変更したら、ドキュメントも変更して！
4. テストを通るようにして`npm test`
5. lintをかけて　`npm lint`
6. コードのフォーマットはprettierに従えて。 `npm run prettier`
7. flowの型チェックもやって　`npm run flow `
8. テストを追加・削除したら、　`./scripts/fiber/record-test`を実行して欲しい。
9. これらのことが終わったらCLAを提出して欲しい

### CLA(Contributor License Agreement)

PRを受け入れるためには、CLAに提出してもらうことが必要となる。
一回だけこれはやれば良い。なので他のオープンソース（FBの)に参加している場合は不要となる。

### Contribution Prerequisites

- node 4.0.0 以上、npm v2.0.0以上
- コンパイルが必要な場合は　gccが必要となる。OSXの場合はXcodeのCommand Line Toolsが必要。

### Development Workflow

Reactをクローンしたら　`npm install` してください。

- `npm run lint` コードのスタイルをチェックする
- `npm test` ユニットテストを実行する
- `npm test -- --watch` テストを監視しながら実行する
- `npm test <pattern>` ファイルネームを指定してテストを実行
- `npm run flow` flowによる型チェック
- `npm run build` 全てのパッケージをビルド

リグレッションを引き起こさないようにするには`npm test`をお勧めする。

最初に `npm run build ` してもらうと、buildフォルダーにpre-buildbundlesがあs区政される。npm packagesはbuild/packagesに格納される。

変更を試す簡単な方法は`npm run build`して、 `fixtures/packaging/babel-standaline/dev.html`を開くこと。このファイルは、ビルドフォルダにあるreactを使用しているため変更内容が反映されている。

もしも、既存のReactプロジェクトに変更したreactを取り入れたいのなら、 `build/dist/react.ldevelopment.js`, `build/dist/react-dom.development.js` あるいは他のビルドしたものをstable-versionの代わりに使用してください。
npmからReactを落として使う場合は、react, react-domを削除して、 `npm link`とつかってローカルのbuildフォルダーにsymlinkを貼ってください

```
cd your_project
npm link ~/path_to_your_react_clone/build/packages/react
npm link ~/path_to_your_react_clone/build/packages/react-dom
```

React folderでnpm run buildした時はいつも、プロジェクトのnode_modulesがアップデートされる。なので、プロジェクトを変更して試すことができる。

PRには、機能的な追加がある場合はユニットテストが必要。
これは将来的にコードを破損的にしないために必要

## StyleGuide

コードにスタイリングの問題がないかは、`npm run lint`をしてコードを精査できます。

しかし、一部のスタイリングについては問題を収集することができない。ので、Airbnb's Style Guideをみてそれに合わせて欲しい。

### Code Conventions

- セミコロンは使って
- コンマは末尾につける
- ノータブで2スペースのインデント
- シングルクォートを好む。
- 'use strict'
- 一ラインの文字列は120以内にする
- 魅力的なコードを書く
- setTimeout, setIntervalは使わない



