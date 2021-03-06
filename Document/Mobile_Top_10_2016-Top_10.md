# Mobile Top 10 2016-Top 10

## [M1 - 不適切なプラットフォームの利用](Mobile_Top_10_2016-M1-Improper_Platform_Usage.md)

このカテゴリはプラットフォーム機能やプラットフォームセキュリティコントロールの正しくない使い方を対象としています。モバイルオペレーティングシステムの一部である、Androidインテント、プラットフォームパーミッション、TouchIDの誤用、キーチェーン、その他のセキュリティコントロールを扱います。
モバイルアプリではさまざまな場面でこのリスクが発生します。

## [M2 - 安全でないデータストレージ](Mobile_Top_10_2016-M2-Insecure_Data_Storage.md)

この新しいカテゴリは Mobile Top Ten 2014 の M2 と M4 を組み合わせたものです。安全でないデータストレージと意図しないデータ漏洩を対象とします。

## [M3 - 安全でない通信](Mobile_Top_10_2016-M3-Insecure_Communication.md)

これは脆弱なハンドシェイク、不適切なSSLバージョン、脆弱なネゴシエーション、機密資産の平文通信などを対象とします。

## [M4 - 安全でない認証](Mobile_Top_10_2016-M4-Insecure_Authentication.md)

このカテゴリはエンドユーザー認証やセッション管理の不備を対象としています。以下を扱います。
- 必要なときにユーザーを特定できない
- 必要なときにユーザーの同一性を維持できない
- セッション管理の不備

## [M5 - 不十分な暗号化](Mobile_Top_10_2016-M5-Insufficient_Cryptography.md)

コードは機密情報資産に暗号を適用します。しかし、暗号は不十分となることがあります。TLSやSSLに関する事項はM3を参照してください。また、アプリが必要なときに暗号を使用できない場合についてはM2を参照してください。このカテゴリは暗号が攻撃される問題に対するものであり、正確性については言及しません。

## [M6 - 安全でない認可](Mobile_Top_10_2016-M6-Insecure_Authorization.md)

これは認可の障害を扱うカテゴリです。認証の問題とは異なります。認可の障害にはクライアントサイドでの認可決定やフォースブラウジングなどがあります。認証の問題にはデバイス登録、ユーザー識別などがあります。

アプリが必要な状況においてまったくユーザーを認証しないのであれば、認可の障害ではなく認証の障害となります。例えば、認証および認可されたアクセスが必要な場合に、一部のリソースやサービスに匿名アクセスを許可することが挙げられます。

## [M7 - 脆弱なコード品質](Mobile_Top_10_2016-M7-Poor_Code_Quality.md)

これはあまり使用されていないカテゴリの一つ「信頼できない入力に対するセキュリティ判定」というものでした。このカテゴリはモバイルクライアントにおけるコードレベル実装の問題を包括することになります。サーバーサイドのコーディングミスとは異なります。モバイルデバイスで動作するコードの書き換えを引き起こす、バッファオーバーフロー、フォーマット文字列脆弱性、その他あらゆるコードレベルの誤りを扱います。

## [M8 - コード改竄](Mobile_Top_10_2016-M8-Code_Tampering.md)

このカテゴリはバイナリパッチ、ローカルリソース変更、メソッドフック、メソッドスウィズリング、動的メモリ変更を対象とします。

アプリケーションがモバイルデバイスに配信されると、コードやデータリソースはそこに常駐します。攻撃者は直接コードを変更したり、動的にメモリ内容を変更したり、アプリケーションが使用するシステムAPIを変更したり置き換えたり、アプリケーションデータやリソースを変更したりします。これによりソフトウェアの意図した使い方を覆す直接的な方法が提供され、攻撃者は個人的もしくは一時的な利益を得ます。

## [M9 - リバースエンジニアリング](Mobile_Top_10_2016-M9-Reverse_Engineering.md)

このカテゴリはソースコード、ライブラリ、アルゴリズム、その他の資産を得るための最終的なコアバイナリの分析を対象とします。IDA Pro、Hopper、otool、その他のバイナリ検査ツールのようなソフトウェアは攻撃者にアプリケーションの内部機能を明らかにします。これは、バックエンドサーバー、暗号定数や鍵、知的財産に関する情報を明らかにするだけでなく、アプリケーションの新たな脆弱性を悪用されることもあります。

## [M10 - 余計な機能](Mobile_Top_10_2016-M10-Extraneous_Functionality.md)

開発者は製品環境に出荷されることを意図しない隠しバックドア機能やその他の内部開発セキュリティコントロールを組み込むことがよくあります。例えば、開発者はハイブリッドアプリのコメントとして誤ってパスワードを組み込むことがあります。他にもテスト中に二要素認証を無効化していることがあります。
