# HTTPにまつわる用語について
## ◎URLとは何か？
[1] URL（Uniform Resource Locator）とは  
- Webサイトのページがどこに位置するのかを示す「住所」のような意味合いで使われる。  
- URLは「http://」や「https://」から始まる。

[2]URLの形式について
- URLは「スキーム」「FQDN」「パス」「クエリパラメータ」など、いくつかの部分に分けられる。

  ```
  サンプルのURL：https://www.example.com/search?q=hello
  ```

| 形式の部分名称 |  |
| :----:| :----: |
| スキーム | https |
|  FQDN[^1] | www.example.com |
| パス | /search |
| クエリパラメータ | ?q=hello |

[^1]:FQDN（Fully Qualified Domain Name：完全修飾ドメイン名）とは、ホスト名（ネットワーク内のコンピューターの名前）とドメイン名（インターネット上のネットワークの名前）を省略せずにつなげて記述した文字列のこと。ドメイン名をマンション名、ホスト名を部屋番号の住所に例えて言うなら、「マンションの住所と部屋番号を繋げて書いた」ものということになる。  

[3] HTTPSとHTTPの違いについて  
- 通信がSSL[^2]によって暗号化されているか否か。暗号化されていれば「HTTPS」、暗号化されていなければ「HTTP」。
[^2]:SSL（Secure Sockets Layer）とは、Webサイトとそのサイトを閲覧しているユーザとのやり取り（通信）を暗号化するための仕組み。現在では、より安全なTLS（Transport Layer Security）という暗号化通信の規格が使われている。

> 引用　https://www.profuture.co.jp/mk/column/53058

## ◎クエリ文字列とは何か？
