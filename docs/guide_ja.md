# ガイド
この文書では、プロファイルのフォルダ名を`{プロファイル名}`、ファイル名を`{ファイル名}`と表記します。

## サーバー管理者向け
### 導入方法
独自の導入方法を指定しているリソースは、その方法に従ってください。

#### プラグイン
1. scssファイルをダウンロードまたはクローンします。
2. Mastodon Materialの[`plugins`](https://github.com/GenbuProject/Mastodon-Material/tree/master/src/mastodon-material/plugins)フォルダにそのファイルを移動します。
3. `profiles/{プロファイル名}/plugins.scss`に次のように追記してください。  
   ```scss
   @import '../../plugins/{ファイル名}';
   ```

#### 配色
1. scssファイルをダウンロードまたはクローンします。
1. Mastodon Materialの[`color`](https://github.com/GenbuProject/Mastodon-Material/tree/master/src/mastodon-material/color)フォルダにそのファイルを移動します。
2. `profiles/{プロファイル名}/config.scss`に次のように追記してください。
   ```scss
   @import '../../color/{ファイル名}';
   ```

#### レイアウト
1. scssファイルをダウンロードまたはクローンします。
1. Mastodon Materialの[`layout`](https://github.com/GenbuProject/Mastodon-Material/tree/master/src/mastodon-material/layout)フォルダにそのファイルを移動します。
2. `profiles/{プロファイル名}/config.scss`に次のように追記してください。
   ```scss
   @import '../../layout/{ファイル名}';
   ```

### アップデート
各手順の2で導入したファイルを、最新のものに置き換えます。  
一部のリソースでは、アップデートの案内がコンソールに表示されることがあります。

## 開発者向け
### 変数について
利用できる変数は[color/v1-light.scss](https://github.com/GenbuProject/Mastodon-Material/blob/master/src/mastodon-material/color/v1-light.scss)や[layout/material-v2.scss](https://github.com/GenbuProject/Mastodon-Material/blob/master/src/mastodon-material/layout/material-v2.scss)などの公式リソースを参照してください。

### フォールバック
バージョンアップや仕様変更により互換性が失われた場合に、公式のリソースを使ってフォールバックすると、互換性の問題を緩和できることがあります。scssファイルの先頭に、以下のように記述してください。参照はファイルの配置に合わせて適宜変更してください。

#### 配色
```scss
@import '../color/{ファイル名}';
```

#### レイアウト
```scss
@import '../layout/{ファイル名}';
```

### プラグインのターゲットバージョンを指定する
Mastodon Materialのバージョンと、プラグインのターゲットバージョンが異なる場合に、コンソールにメッセージを表示させることができます。scssファイルの先頭に以下のように記述してください。
```scss
$name: "プラグイン名";  // プラグイン名
$plugin-version: "1.0.0";  // プラグインのバージョン
$target-version: "1.0.0";  // theme/theme.scssの$versionを確認
$website: "";  // ウェブサイトまたはダウンロードURL
@include version-check($name, $plugin-version, $target-version, $website);
```

### 貢献の方法
製作したリソースをこのリポジトリに載せる場合、以下の様式に従ってプルリクエストを開いてください。
- 最低限、リソース名、説明(言語の種類、数は問わない)、バージョンをプルリクエストのコメントに記述してください。[README.md](../README.md)に載ります。スクリーンショットを1枚まで含めることができます。
- ファイルが複数ある場合、1つのフォルダに入れてください。階層は自由です。
- scssファイルのほかに、以下のファイルを含めることができます。
  - README
  - スクリーンショット
  - LICENSEファイル