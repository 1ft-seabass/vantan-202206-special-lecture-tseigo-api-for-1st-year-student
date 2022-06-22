# API で大切な HTTP

## API の多くは HTTP プロトコルでできている



## HTTP について

HTTP プロトコルについて概要を把握します。

HTTP は Hypertext Transfer Protocol という正式名称です。 Web ブラウザが Web サーバと通信する際に主として使用する通信プロトコルです。

よくある例としては、みなさんが Web ブラウザからアドレスバーで URL を入力して HTML などのテキストによって記述された Web ページなどのコンテンツを表示するときのデータの送受信に用いられます。

参考文献
- Hypertext Transfer Protocol - Wikipedia
  - https://ja.wikipedia.org/wiki/Hypertext_Transfer_Protocol
- HTTP の基本 - HTTP | MDN
  - https://developer.mozilla.org/ja/docs/Web/HTTP/Basics_of_HTTP

実際には、このような仕組みになっています。

> HTTPはリクエスト-レスポンス型のプロトコルであり、クライアントがサーバにリクエストメッセージを送信する。 基本的な考え方は非常に単純で、「何を」「どうして」欲しいのかを伝える。URLが「何を」、メソッドが「どうして」に当たる。 サーバはこれにレスポンスメッセージを返し、基本的にこの時点で初期状態に戻る。つまり、サーバはクライアントの状態を保存しない。
>
> Hypertext Transfer Protocol - Wikipedia - https://ja.wikipedia.org/wiki/Hypertext_Transfer_Protocol

この説明は、仕様をちゃんと説明してはいるのですが、ちょっととっつきにくいかもしれません。もう少し、噛み砕いていきましょう。

![image](https://i.gyazo.com/8d8b5bcd165aa9851160c0aeac32169d.png)

こちらの図を見つつ、[典型的な HTTP セッション](https://developer.mozilla.org/ja/docs/Web/HTTP/Session) を追っていきます。

まず、クライアントからサーバーへ URL で「何か」決めて問い合わせます。また、HTTP ヘッダーでクライアントからサーバーが追加情報を渡すことができます。

- HTTP メソッド
  - リソースに対して実行したいアクションを宣言します。いろいろありますが GET と POST を使うことが多いです。
  - https://developer.mozilla.org/ja/docs/Web/HTTP/Headers
- HTTP ヘッダー
  - HTTP リクエストやレスポンスでクライアントやサーバーが追加情報を渡すことができます
  - https://developer.mozilla.org/ja/docs/Web/HTTP/Headers

![image](https://i.gyazo.com/03d1c316f872a525a4bb30e7fffa412a.png)


そして、サーバーが HTTP リクエストから受け取った内容で、今度は HTTP レスポンスという形で応答します。こちらの図を見つつ、[典型的な HTTP セッション](https://developer.mozilla.org/ja/docs/Web/HTTP/Session) を追っていきます。

まず、HTTP ヘッダーでサーバーからクライアントへ追加情報を渡すことができます。そして、HTTP 応答ステータスコードで正常に完了したどうかを伝えます。こちらを、みなさんのブラウザが受信すると Web ページが表示されます。

- HTTP 応答ステータスコード（HTTP レスポンスステータスコード）
  - 特定の HTTP リクエストが正常に完了したどうかを示します。200 が Success で応答成功です。その他に、有名なものとして 404 , 500 , 503 などがあります。
  - 404 Not Found
    - サーバーがリクエストされたリソースを発見できないこと
  - 500 Internal Server Error
    - サーバー側で処理方法がわからない事態が発生したことを示します。
  - 503 Service Unavailable
    - サーバーはリクエストを処理する準備ができていないことを示します。
  - 参考文献（一覧はこちら）
    - https://developer.mozilla.org/ja/docs/Web/HTTP/Status

全体の図としては以下の通りです。

![image](https://i.gyazo.com/6052386b6f5bdf2b17b7692149fd2d92.png)

本来、みなさんのブラウザで URL にアクセスして何かしらが表示されるまでには、このような流れで行われています。いろいろありますね。

ですが、いま、すべて覚える必要はないです。 HTTP プロトコルを扱うために、ざっくりこのような流れになっているんだなと理解できていれば OK です。

雰囲気での理解は、あとで生きてきます！

## Unity における HTTP 



## 今回は HTTP GET で 1 点突破します

次の章では、ブラウザで表示して確認もできる GET リクエストの API でサッと試してみます。

柴犬画像をランダムで表示する API に Unity からつなぎます。

