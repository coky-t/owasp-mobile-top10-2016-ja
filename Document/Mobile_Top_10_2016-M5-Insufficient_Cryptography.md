# Mobile Top 10 2016-M5-不十分な暗号化

| 脅威エージェント |
| --- |
| アプリケーション依存 |
| 脅威エージェントには、不適当に暗号化されたデータへの物理的アクセスを行う者や、攻撃者に代わって動作するモバイルマルウェアがあります。 |

| 攻撃手法 |
| --- |
| 悪用難易度 容易 |
| 攻撃手法には、デバイスへの物理的アクセスやネットワークトラフィックキャプチャを介したデータの復号や、暗号化されたデータにアクセスするデバイス上の悪意のあるアプリがあります。 |

| セキュリティ上の弱点 |
| --- |
| 普及度 中, 検出難易度 普通 |
| この脆弱性を悪用するには、攻撃者は暗号化プロセス内の脆弱な暗号化アルゴリズムや欠陥により、暗号化されたコードや機密データを元の暗号化されていない形式に正常に戻す必要があります。 |

| 技術的影響 |
| --- |
| 影響度 深刻 |
| この脆弱性により、モバイルデバイスから機密情報を不正に取得される可能性があります。 |

| ビジネスへの影響 |
| --- |
| アプリケーション / ビジネス依存 |
| この脆弱性にはさまざまなビジネスへの影響があります。通常、不完全な暗号化は以下をもたらします。 |

- プライバシー侵害
- 情報漏洩
- コード漏洩
- 知的財産漏洩
- 風評被害

---

## &#39;不十分な暗号化&#39;の脆弱性があるか？

暗号化を利用するモバイルアプリでは暗号化の安全でない利用が一般的です。モバイルアプリ内での不完全な暗号化には基本的に2つの現れ方があります。1つ目は、モバイルアプリは根本的に欠陥がある暗号化/復号化を元にした処理をしており、攻撃者により機密データの復号に悪用されてしまうというものです。2つ目は、モバイルアプリは本質的に脆弱である暗号化/復号化アルゴリズムを実装または利用しており、攻撃者により直接解読されてしまうというものです。以下のサブセクションではこれらのシナリオの両方をさらに詳しく説明します。

### ビルトインコード暗号化プロセスへの依存

デフォルトでは、iOS アプリケーションはコード暗号化により(理論上は)リバースエンジニアリングから保護されています。iOS セキュリティモデルでは非脱獄環境で実行するために、アプリは信頼できるソースにより暗号化および署名される必要があります。起動時に、iOS により署名が検証された後に、iOS アプリローダーはメモリ内にアプリを復号化してコードを実行します。この機能は、理論上、攻撃者が iOS モバイルアプリに対してバイナリ攻撃を行うことを防ぎます。

ClutchMod や GBD などの自由に利用できるツールを使用して、攻撃者は暗号化されたアプリを脱獄されたデバイス上にダウンロードし、iOS ローダーがメモリにロードし復号化したアプリのスナップショットを(ローダーが実行を開始する直前で)取得します。攻撃者はスナップショットを取得してディスクに格納すると、IDA Pro や Hopper などのツールを使用してアプリの静的/動的分析を簡単に実行し、さらにバイナリ攻撃を行うことができます。

ビルトインコード暗号化アルゴリズムをバイパスすることはとても簡単なことです。常に攻撃者は根底にあるモバイル OS により提供されるビルトインコード暗号化をバイパスできると想定します。
リバースエンジニアリング防止の追加レイヤーを提供するための追加のステップについては M9 を参照のこと。

#### 脆弱な鍵管理プロセス

あなたが鍵を誤って扱うのであれば、最高のアルゴリズムは関係ありません。正しい暗号化アルゴリズムですが、それを使用する独自のプロトコルを実装するという間違いを犯すことが多くあります。ここでの問題の例をいくつか挙げます。

- 暗号化されたコンテンツとして攻撃者が読み取り可能な同じディレクトリに鍵を置くこと
- 鍵を作成したが攻撃者に利用可能であること
- バイナリ内にハードコードされた鍵を使用すること
- 鍵はバイナリ攻撃により傍受される可能性があります。バイナリ攻撃を防ぐ方法の詳細については M9 を参照ください。

#### カスタム暗号化プロトコルの作成と利用

モバイルなどで暗号化を誤って扱う以上に、独自の暗号化アルゴリズムやプロトコルの作成および使用を試みることは簡単に誤って処理してしまいます。

セキュリティコミュニティにより強固であるとして受け入れられている最新のアルゴリズムを常に使用し、可能な限りモバイルプラットフォーム内の最先端の暗号化 API を活用してください。バイナリ攻撃によりバイナリ内にハードコードされた鍵とともに利用する共通ライブラリを攻撃者に特定される可能性があります。暗号化に対するセキュリティ要件が非常に高い場合は、ホワイトボックス暗号の利用を積極的に検討すべきです。共通ライブラリの悪用につながるバイナリ攻撃を防止する方法については M9 を参照してください。

#### 安全でない/廃止されたアルゴリズムの利用

多くの暗号化アルゴリズムやプロトコルは重大な脆弱性があることが示されていたり、現代のセキュリティ要件には不十分であるため、使用してはいけません。これらには以下があります。

- RC2
- MD4
- MD5
- SHA1

---

## &#39;不十分な暗号化&#39;を防ぐには？

機密データを扱う場合、以下のようにすることが最善です。

- 可能であればモバイルデバイス上での機密データの格納を避けること。
- 今後10年以上のテストに耐えられる暗号規格を適用すること。
- 推奨アルゴリズムに関する NIST ガイドラインに準拠すること。(参考資料のその他を参照ください)

---

## 攻撃シナリオの例

---

## 参考資料

**OWASP**

- [OWASP Cryptographic Storage Cheat Sheet](https://www.owasp.org/index.php/Cryptographic_Storage_Cheat_Sheet) [(和訳)](https://jpcertcc.github.io/OWASPdocuments/CheatSheets/CryptographicStorage.html)
- [OWASP Key Management Cheat Sheet](https://www.owasp.org/index.php/Key_Management_Cheat_Sheet) [(和訳)](https://jpcertcc.github.io/OWASPdocuments/CheatSheets/KeyManagement.html)

**その他**

- [NIST Encryption Guidelines](http://csrc.nist.gov/publications/drafts/800-175/sp800-175b_draft.pdf)