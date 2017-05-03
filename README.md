# コントリビュートの方法

## 行動規定
フルテキストはこちら（FacebookにおけるOSSの貢献方法）  
https://code.facebook.com/pages/876921332402685/open-source-code-of-conduct

どのような行為が許可されるのかは、以下に記載する。

## Open Development
作業はすべてGithub上で行われる。  
コアチームと外部貢献メンバーの両方が、同じプロセスを経てPRが送られる。

## Branch Organization
マスターブランチがメインブランチ。  
テストは常に通るようにしておくこと。  
ただし、速やかに移行するためにアプリケーションの互換性のないAPIの変更を行う。  
latest stable varsionにしておくことがおすすめ。

## Semantic versioning

ReactではSemantic versioningを採用している。
全てのPRにはタグをつけている。

## Bugs
### New Issues
issue管理にはgithub issueを使用している。  
新しく追加するときにはすでに登録されていないか注意してほしい。

### Rporting New Issues
できるだけ、テストケースを追加しないでバグを修正するのがとても良い方法。  

https://jsfiddle.net/84v837e9/  
こちらがstarting pointとしてオススメ。

### Security Bugs
FBはbounty program(バグ報酬制度)をセキュリティバグにたいして適用している。  
ただし、これについてはpublicなissueとしてはあげないで欲しい。

## Your First Pull Request
簡単なissueは　`Difficulty: beginner` というタグがつけられている。  
初めてのコントリビュートにおすすめのもの。

issueを治すことをきめたら、コメントを確認して欲しい。  
すでに誰かそれを治す作業をしているかもしれない。  
もし誰も作業していないのならば、「治すよー！」という旨を伝えるコメントを残して欲しい。  
そうすれば、無駄がなくなる。

誰かが、問題提起して2週間以上フォローアップしていない場合は引き継ぐのがいいが、コメントは残して欲しい。

## Sending a pull request
コアチームはPRを見ている。  
コアチームはPRをレビューして、マージする。  
APIの変更についてはFBでの社内利用のための修正が必要な場合があるので少し遅れるかもしれない。  
全てのプロセスを通じて最良のことは行うつもり。

### Before submitting a pull requeset

1. masterからフォークする
2. コードを書き加えたらテストを追加する
3. APIを変更したら、ドキュメントも変更する
4. テストを通るようにして `npm test`
5. lintをかけて　`npm lint`
6. コードのフォーマットはprettierに従えて `npm run prettier`
7. flowの型チェックもやって　`npm run flow`
8. テストを追加・削除したら、　`./scripts/fiber/record-test` を実行する
9. これらのことが終わったらCLAを提出する

### CLA(Contributor License Agreement)

PRを受け入れるためには、CLAに提出してもらうことが必要となる。
CLAの提出は、一度行えばいい。  
なので他のオープンソース（FBの)に参加している場合は不要となる。

### Contribution Prerequisites

- node 4.0.0 以上、npm v2.0.0以上
- コンパイルが必要な場合は　gccが必要となる。OSXの場合はXcodeのCommand Line Toolsが必要

### Development Workflow

Reactをクローンしたら　`npm install` する。

- `npm run lint` コードのスタイルをチェックする
- `npm test` ユニットテストを実行する
- `npm test -- --watch` テストを監視しながら実行する
- `npm test <pattern>` ファイルネームを指定してテストを実行
- `npm run flow` flowによる型チェック
- `npm run build` 全てのパッケージをビルド

リグレッションを引き起こさないようにするには`npm test`をお勧めする。

最初に `npm run build` してもらうと、buildフォルダーにpre-buildbundlesが作成される。  
npm packagesはbuild/packagesに格納される。

変更を試す簡単な方法は `npm run build` して、 `fixtures/packaging/babel-standaline/dev.html` を開くこと。  
このファイルは、ビルドフォルダにあるreactを使用しているため変更内容が反映されている。

もし、既存のReactプロジェクトに変更したreactを取り入れたいのなら、 `build/dist/react.development.js`, `build/dist/react-dom.development.js` あるいは他のビルドしたものをstable-versionの代わりに使用する。  
npmからReactを落として使う場合は、react, react-domを削除して、 `npm link`とつかってローカルのbuildフォルダーにsymlinkを貼る。

```sh
cd your_project
npm link ~/path_to_your_react_clone/build/packages/react
npm link ~/path_to_your_react_clone/build/packages/react-dom
```

React folderで `npm run build` した時はいつも、プロジェクトのnode_modulesがアップデートされる。  
なので、プロジェクトを変更して試すことができる。

PRには、機能的な追加がある場合はユニットテストが必要。  
これは将来的にコードを破損させないために必要。

## StyleGuide

コードにスタイリングの問題がないかは、`npm run lint`をしてコードを精査できる。
しかし、一部のスタイリングについては問題を収集することができない。  
なので、Airbnb's Style Guideをみてそれに合わせて欲しい。

### Code Conventions

- セミコロンを使う
- コンマは末尾につける
- ノータブで2スペースのインデント
- シングルクォートを好む
- 'use strict'
- 1ラインの文字列は120文字以内にする
- 魅力的なコードを書く
- setTimeout, setIntervalは使わない



