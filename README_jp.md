# ロボカップ小型機リーグルール

[English](README.md) | Japanese  

ロボカップ小型機リーグ(SSL)ルールの非公式日本語訳の、AsciiDoc形式のソースコードです。  
公式ルールは、[小型機リーグ公式GitHubリポジトリ](https://github.com/RoboCup-SSL/ssl-rules)よりご覧いただけます。  
旧バージョンのルール(英語)は[こちら](https://github.com/RoboCup-SSL/ssl-rules-legacy)よりご覧いただけます。

## ビルド

ルールはmaster-jpブランチの更新に応じて、自動的に[Github Page](https://kkimurak.github.io/ssl-rules-ja/sslrules.html)に公開されます。[PDF版](https://kkimurak.github.io/ssl-rules-ja/sslrules.pdf)もご利用いただけます。  
組み込み属性（「図」、「目次」など）に翻訳を適用するために、AsciiDocの機能である["Include Content from a URI"](https://asciidoctor.org/docs/user-manual/#include-uri)を使用しているため、`allow-uri-read`オプションを使用する必要があります。

### ネイティブ版AsciDoctorの使用

[AsciiDoctor](https://asciidoctor.org/)をインストールしてください。その後、以下のコマンドでHTML5版をビルドできます。日本語などを含む文章の場合、 attribute `scripts=cjk` を設定することで改行などが改善されます :

```sh
# HTML5版のビルド
asciidoctor -a allow-uri-read -a scripts=cjk sslrules.adoc
```

日本語を含むPDFを生成する場合、日本語フォントを指定したテーマ(特にこだわりがなければデフォルトテーマ)を使うと良いでしょう :

```sh
# Build the PDF version
asciidoctor-pdf -a allow-uri-read -a scripts=cjk -a pdf-theme=default-with-font-fallbacks sslrules.adoc
```

### dockerイメージの使用

Dockerをインストールしているのであれば、日本語環境向けに最適化されたAsciiDoctorイメージを使うことができます :

```sh
# dockerイメージをpullする
docker pull htakeuchi/docker-asciidoctor-jp
# HTML5版のビルド
docker run -v $PWD:/documents/ htakeuchi/docker-asciidoctor-jp asciidoctor -a allow-uri-read sslrules.adoc
# Build the PDF version
docker run -v $PWD:/documents/ htakeuchi/docker-asciidoctor-jp asciidoctor-pdf -r asciidoctor-pdf-cjk-kai_gen_gothic -a pdf-style=KaiGenGothicJP -a allow-uri-read sslrules.adoc
```
