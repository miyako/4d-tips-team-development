# 4d-tips-team-development

### アプリケーションをチームで開発したい場合，どのような選択肢がありますか

1. バイナリモード vs プロジェクトモード
2. 4D or 4D Server
3. ローカルクライアント vs リモートクライアント
4. Team Developer Professional vs Developer Professional ライセンス

#### プロジェクトモード vs バイナリモード

[4Dでデータベースアプリケーションを作成する](https://doc.4d.com/4Dv18/4D/18/Creating-a-new-database.300-4575701.ja.html)場合，単一のストラクチャファイル（拡張子`.4DB`）を使用する**バイナリモード**，または多数のテキストファイルを使用する**プロジェクトモード**のいずれかを最初に選択します。[ストラクチャファイルをプロジェクトに変換する](https://doc.4d.com/4Dv18/4D/18/Converting-databases-to-projects.300-4606146.ja.html)ことはできますが，その逆，つまりプロジェクトをストラクチャファイルに変換することはできません。今後，**新機能**は原則的にプロジェクトモードで提供されることになります。一方，バイナリモードでは（技術的に可能な限り）さまざまな旧式の仕様が引き続きサポートされます。

**注記**: バージョン18 R4以降，プロジェクトモードが既定のフォーマットとなりました。バイナリモードのアプリケーションを作成するためには，アプリケーションの**環境設定**で「バイナリー形式のデータベース作成を有効化する」チェックボックスを有効にする必要があります。

プロジェクトモードは，全面的にテキストファイルを使用するため，**バージョン管理システム**（VCS）を活用したチーム開発に向いています。たとえば，チームのメンバーが個別に実施した変更を統合したり，選択的に採用したりすることができます。一方，バイナリモードはクライアント/サーバーの排他的にアクセス管理を活用した**ライブ開発**ができるというメリットがあります。

* バイナリモードのチーム開発

ストラクチャファイル（`.4DB`）をサーバーで開きます。デベロッパーはそれぞれクライアントを起動してサーバーに接続し，フォームエディターやメソッドエディターでアプリケーションを編集します。誰かがエディターで開いているフォームやメソッドはロックされ，別のデベロッパーは編集できません。フォームやメソッドには[アクセスグループ](https://doc.4d.com/4Dv18/4D/18/Assigning-a-group-to-database-objects.300-4575496.ja.html)を設定することもできます。

![v18-version-control 020](https://user-images.githubusercontent.com/1725068/110051746-c1cf7900-7d99-11eb-8009-a70cf76b3001.jpeg)

**メリット**: 運用中のアプリケーションに修正を加えることができ，変更の内容はすぐに反映されます。ハイライトボタン・ピクチャボタン・スタンドアロン版でのパスワード管理・スクロールエリア風に結合されたリストボックスなど，プロジェクトモードで廃止された旧式の仕様が引き続き使用できます。

**デメリット**: サーバーに接続する必要があるので，デベロッパーはオンラインでなければなりません。当然，クライアント接続ライセンスも消費します。変更を取り消したい場合，バックアップからストラクチャファイルを復元しなければなりません。変更の履歴は，スプレッドシートなどで独自に管理する必要があります。クラス・CSS・Apple Silicon向けのコンパイル（v19）など，プロジェクトモード限定の新しい機能が使用できません。

**注記**: バイナリモードのホストにプロジェクトモードのコンポーネントをインストールすることにより，部分的に利用できるものもあります。

* プロジェクトモードのチーム開発

それぞれのデベロッパーがプロジェクトを開きます。開発に4D Serverは使用しません。メソッド（拡張子`.4DM`），フォーム（拡張子`.4DForm`），スタイルシート（`.css`）など，ソースコードはすべて標準テキストファイルなので，お気に入りのコードエディターや統合開発環境で編集したり，Git，Perforce, Subversionなどのバージョン管理システムでホストしたりすることができます。

![v18-version-control 045](https://user-images.githubusercontent.com/1725068/110053871-74550b00-7d9d-11eb-9472-f2d4735ff3b9.jpeg)
