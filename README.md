# FLOCSS template

## 環境

 Prettier + ESlint + eslint-config-airbnb-base + Stylelint + husky

# Usage

## node package をインストールします。

```
npm install
```

## husky をインストールします。

```
npm run prepare
```

## Sass と tailwindcss を監視します。

```
npm run watch
```

### 🛑 終了コマンド

``` controle + c ``` で watch を終了します。


## JavaScript と CSS, Scss を整形します。

```
npm run format
```

## Git commit 時にフォーマットが走ります。

コミットはターミナルから行ってください。

❗ GUI ツールを使うと husky が走りません。



# 仕様

## CSS

### 📌 Sass コンパイル
```src/style/``` 内の .scss ファイルをの変更を監視して、 ```dist/styles/``` に出力

### 📌 Sass, CSS フォーマット、構文チェック
💻 ``` npm run format ``` でフォーマット、構文チェック、整形を行う。

💻 ```git push``` タイミングでフォーマット、構文チェック、整形、CSS プロパティの順番をソートする。
# package.json の説明
## JavaScript

### 📌 JavaScript フォーマット、構文チェック
💻 ``` npm run format ``` でフォーマット、構文チェック、整形を行う。

💻 ```git push``` タイミングでフォーマット、構文チェック、整形を行う。
# package.json の説明

❗ 以下コードでは説明のために JSON ファイルにコメントを記述しています。通常 JSON ファイルはコメントを扱えません。

```json
{
  "name": "tailwindcss-sass-hans-on", // プロジェクトの名前
  "version": "1.0.0", // プロジェクトのバージョン
  "description": "## 作業ディレクトリの作成", // プロジェクトの説明
  "main": "index.js", // メインのエントリーポイントファイル
  "scripts": {
    "watch": "npm run watch:sass & npm run watch:tailwindcss", // ファイルの変更を監視するためのスクリプト
    "watch:tailwindcss": "npx tailwindcss -i ./src/tailwindcss-input.css -o ./dist/styles/tailwind.css --watch", // Tailwind CSSの変更を監視するためのスクリプト
    "watch:sass": "sass --no-source-map --watch src/styles/:dist/styles/", // Sassファイルの変更を監視するためのスクリプト
    "format": "eslint src --fix && stylelint 'src/**/*.scss' --fix && prettier --write src", // コードの整形を行うためのスクリプト
    "prepare": "husky install" // huskyのインストールを行うためのスクリプト
  },
  "keywords": [], // プロジェクトのキーワード
  "author": "", // プロジェクトの作者
  "license": "ISC", // プロジェクトのライセンス
  "volta": {
    "node": "18.16.0" // 使用するNode.jsのバージョン
  },
  "devDependencies": {
    // 開発時に必要な依存関係の一覧
    "eslint": "^8.41.0", // ESLintのバージョン
    "eslint-config-airbnb-base": "^15.0.0", // Airbnbのスタイルガイドに基づくESLintの設定
    "eslint-config-prettier": "^8.8.0", // ESLintとPrettierの共存に関する設定
    "husky": "^8.0.3", // Gitフックを使用するためのツール
    "lint-staged": "^13.2.2", // ステージングエリアのファイルに対してコマンドを実行するためのツール
    "prettier": "^2.8.8", // コードの整形ツール
    "sass": "^1.62.1", // Sassのバージョン
    "stylelint": "^15.6.2", // CSSの静的解析ツール
    "stylelint-config-recess-order": "^4.0.0", // CSSプロパティの順序に関するスタイルガイド
    "stylelint-config-standard": "^33.0.0", // 標準的なCSSスタイルガイドの設定
    "stylelint-config-standard-scss": "^9.0.0", // SCSSファイルに対するスタイルガイドの設定
    "stylelint-prettier": "^3.0.0", // stylelintとPrettierの共存に関する設定
    "stylelint-scss": "^5.0.0", // SCSSファイルに対するstylelintの設定
    "tailwindcss": "^3.3.2" // Tailwind CSSのバージョン
  },
  "lint-staged": {
    // lint-stagedの設定
    "*.js": [
      "prettier --write", // jsファイルに対してPrettierで整形する
      "eslint --fix" // jsファイルに対してESLintで静的解析と整形を行う
    ],
    "*.{scss,css}": [
      "stylelint --fix" // scss、cssファイルに対してstylelintで静的解析と整形を行う
    ]
  }
}
```

# FLOCSS に独自のルールを追加

utility　は tailwindcss のルールセットを使う

リポジトリ内で完結するプロジェクトでは tailwindcss の JIT を使う
リポジトリを横断するようなプロジェクトでは tailwindcss を動的に生成するのではなく、
最低限だけ抜粋して記述する（※下記範疇に留める）。


>　3. Utility
>　ComponentとProjectレイヤーのObjectのモディファイアで解決することが難しい・適切では無い、わずかなスタイルの調整のための便利クラスなどを定義します。
>　
>　Utilityは、Component、ProjectレイヤーのObjectを無尽蔵に増やしてしまうことを防いだり、またこれらのObject自体が持つべきではないmarginの代わりに.mbs { margin-bottom: 10px; }のようなUtility Objectを用いて、隣接するモジュールとの間隔をつくるといった役割を担います。
>　
>　またclearfixテクニックのためのルールセットが定義されているヘルパークラスも、このレイヤーに含めます。






---



# 参考


### ✅ ESLint

📝 [eslintとprettierの組み合わせ](https://zenn.dev/kohski/articles/eslint-prettier-integration)
### ✅ Stylelint

📝 [｢Stylelint｣｢Prettier｣を使ってコードの品質を高める【2023年版】](https://okalog.info/stylelint/#index_id5)
### ✅ Prettier

📝 [Prettierの導入方法 フロントエンド開発で必須のコード整形ツール](https://ics.media/entry/17030/#eslint%E3%81%A8%E9%80%A3%E6%90%BA%E3%81%97%E3%81%A6%E3%83%95%E3%82%A9%E3%83%BC%E3%83%9E%E3%83%83%E3%83%88%E3%82%92%E9%81%A9%E7%94%A8%E3%81%99%E3%82%8B)

📝 [PrettierとESLint・Stylelintの併用](https://rinoguchi.net/2021/12/prettier-eslint-stylelint.html)



📝 [.prettierrc](https://qiita.com/takeshisakuma/items/bbb2cd2f1c65de70e363) : 設定ファイルの種類

### ✅ eslint-config-airbnb-base

📝 [手軽に eslint-config-airbnb を導入](https://qiita.com/sugx2/items/ed58605e4e12519876fd) : Vanilla JS で Aribnb Style Lint を使う

### ✅ husky

📝 [commit 時に ESlint と Prettier を実行する【ESLint】【Prettier】](https://qiita.com/P-man_Brown/items/c2a04dc1bdbd78b44fef)

📝 [husky v6 のインストール方法と使い方。lint-staged も導入して、品質を保とう](https://fwywd.com/tech/husky-setup)
[]()

---

