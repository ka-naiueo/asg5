# HTTPにまつわる用語について
## ◎URLとは何か？
**[1] URL(Uniform Resource Locator)とは** 
- Webサイトのページがどこに位置するのかを示す「住所」のような意味合いで使われる。
  
- URLは「http://」や「https://」から始まる。

**[2]URLの形式について**
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

**[3] HTTPSとHTTPの違いについて**  
- 通信がSSL[^2]によって暗号化されているか否か。暗号化されていれば「HTTPS」、暗号化されていなければ「HTTP」。
[^2]:SSL（Secure Sockets Layer）とは、Webサイトとそのサイトを閲覧しているユーザとのやり取り（通信）を暗号化するための仕組み。現在では、より安全なTLS（Transport Layer Security）という暗号化通信の規格が使われている。

> 参照：[Marke TRUNK](https://www.profuture.co.jp/mk/column/53058)

## ◎クエリ文字列とは何か？
クエリ文字列（URLパラメーター）とは  
- サーバーに情報を送るためにURLの末尾につけ足す文字列（変数）のこと。
  
- 「?」をURLの末尾につけ、その次に「パラメーター＝値」をつけ、複数のパラメーターをつけたい場合は「&」を使用する。
  
- クエリ文字列にはWebサイトのアクセス解析を行なってくれる「パッシブパラメーター」と動的なページ結果の表示を行なってくれる「アクティブパラメーター」の２種類がある。
  
- ユーザーの流入元（自然検索で入ってきたのか、広告から入ってきたのか）が分かったり、ユーザーの足跡のヒントをくれる。

```
  サンプルのURL 「https:// ○△×□.jp/?●=▲×■&○=△×□」
                         ↓
　　　　　　　　　　　「?●=▲×■&○=△×□」の部分がクエリ文字列
```

>　参照：[デジハリONLINE](https://online.dhw.co.jp/kuritama/query-string/)

## ◎パス変数（パスパラメーター）とは何か?  
- ディレクトリやファイルへのショートカット

> 参照：[JMP STATISTICAL DISCOVERY](https://www.jmp.com/support/help/ja/17.2/index.shtml#page/jmp/path-variables.shtml)

## ◎クエリ文字列とパス変数の違いとは  

**[1] クエリ文字列とは**  

- 省略可能な付加情報のことで、検索・フィルタなどプラスアルファの条件を付け足したい時に用いる。

- ルートパスの一部ではないので、?を付け足してその後ろに記載。

```
クエリ文字列　→ ?page=2&sort=false の部分
http://example.com/path/param1/?page=2&sort=false
```

**[2] パス変数**  
- 特定のリソースを特定して表示する際に用いる。

- ルートパスの一部として、スラッシュの後に付け足すだけ。

```
パス変数　→ param1の部分
http://example.com/path/param1
```

> [!Note]  
> クエリ文字列　→ 特定のものに条件を加える場合に必要  
> パス変数　→ 特定のものを表示したい場合に必要   

> 参照：[Zenn パスパラメータとクエリパラメータの違い](https://zenn.dev/eri_agri/articles/859a3362db8386)    
> 　　：[Zenn パスパラメータとクエリパラメータ](https://zenn.dev/y__adler/articles/7a73cdf4c1987a)

## ◎HTTPメソッドとは何か?  

- クライアントコンピューターのブラウザから送信され、どのリソースに対して何をしたいかを指示するもの。
 
- 「どの」リソースかは、URLで決定されるが、「何をしたいか」は別に指示する必要がある。

- HTTPリクエストを受け取ったサーバは、HTTPメソッドが指示されることで、クライアントから何を求められているかがわかる。

|HTTPメソッド|はたらき|
|:----|:----|
|GET|リソース情報を取得する|
|POST|新しいリソース情報を送り込む|
|PUT|リソース情報を新しい情報で置き換える|
|PATCH|リソース情報の一部を新しい情報で書き換える|
|DELETE|リソース情報を削除する|  

> 参照：[DPro](https://diveintocode.jp/blogs/Technology/depUrlHttpMethod#:~:text=HTTP%E3%83%A1%E3%82%BD%E3%83%83%E3%83%89%E3%81%AF%E3%80%81%E5%AF%BE%E8%B1%A1%E3%81%A8,%E3%81%AE2%E7%A8%AE%E9%A1%9E%E3%81%A7%E3%81%82%E3%82%8B%E3%80%82)

## ◎リクエストヘッダーとは何か?  
- HTTPリクエストは以下の図の３つから構成されている。リクエストヘッダーはその内の１つ。
  
- 取得するリソース又はクライアント自体に関する詳細情報を含むヘッダー（お願いごとやお願い元に関する情報が書かれている場所）。
   
- 書式は【フィールド名】:【内容】となっている。

![ HTTPリクエストヘッダー](https://github.com/ka-naiueo/asg5/assets/161119501/19a4ed69-85d9-4ed0-a7bf-2a6c18a81c4f)  

> 参照：[わわわIT用語辞典](https://wa3.i-3-i.info/word1844.html)   
> 　　：[Mdn Web Docs](https://developer.mozilla.org/ja/docs/Glossary/HTTP_header)

## ◎HTTPステータスコードとは何か？   
**[1] HTTPステータスコードとは**  
- HTTPレスポンスに含まれるWebサーバーの処理結果を表現する3桁の数字のことを指す。
  
- HTTPステータスコードは大きく分けると1xx、2xx、3xx、4xx、5xxの5つに大別できる。

|HTTPステータスコード|意味|
|:---|:---|
|1xx:処理中(Informational)|情報処理中であるということを示す|
|2xx:成功（Success)|通信が成功したことを示す|
|3xx:リダイレクト(Redirection)|リダイレクト（転送）がおこなわれたことを示す|
|4xx:クライアントエラー（Client errors）|クライアント側でエラーが起きていることを示す|
|5xx:サーバーエラー（Server errors）|サーバー側でエラーが起きていることを示す|  

**[2] 主要なHTTPステータスコード**  

|HTTPステータスコード|意味|  
|:---|:---|
|200 OK|リクエスト成功|
|201 Created|リクエストが成功し、リソースの作成が完了|
|400 Bad Request|リクエストが無効|
|404 Not Found|リソース・ページが存在しない|
|500 Internal Server Error|サーバー内部エラー|  

> 参照：[DIGIFUL](https://digiful.irep.co.jp/blog/76975541525)

## ◎レスポンスヘッダーとは何か？　レスポンスボディとは何か?   

**[1] HTTPレスポンスヘッダーとは**  
- HTTPレスポンスは以下の図のように３つの構成に分けられる。レスポンスヘッダーはその内の１つで真ん中の部分。
   
- レスポンスについての追加情報、例えば場所やサーバー自身についての情報 (名前、バージョン、など) を含むヘッダー。   
 （ステータスラインに書ききれないレスポンスの情報が書かれている場所）。

- 書式はリクエストヘッダーと同様で【フィールド名】:【内容】となっている。    

**[2] HTTPレスポンスボディとは**  
- HTTPレスポンスの３つに分けられた内の一番下の部分。

- リクエストされたURLに対するHTMLや画像などのデータが記載される。  
　（相手が欲しがってたファイル[HTMLファイル]の中身が書いてある場所）。

![ HTTPレスポンスヘッダー](https://github.com/ka-naiueo/asg5/assets/161119501/66ddfef5-107e-4ba7-9f76-e85358d8ba24)

> 参照：[わわわIT用語辞典](https://wa3.i-3-i.info/word1847.html)   
> 　　：[MDN Web docs](https://developer.mozilla.org/ja/docs/Glossary/HTTP_header)    
> 　　：[Zenn 【AWS④】 HTTPの動きについて理解を深める](https://zenn.dev/oreo2990/articles/145437fa43a001)

## ◎JSON（JavaScript Object Notation）とは何か?  

**[1]　JSONとは**

- JavaScriptというプログラミング言語におけるオブジェクトの書き方を参考に作られたデータフォーマット(データの記述形式)のこと。
  
- 人間とコンピューターの双方にとって可読性が高く、データが重くなりづらいという優れた特徴を持つ。

**[2] 用途**
  
- データを保存するための形式としてよく使用されている。
  
- テキストを用いたデータ表記方法の為非常に汎用性が高く、異なる言語、環境の間でデータの受け渡しや共有をする時に役立つ。

**[3] 記述形式**

- JSONの記述形式は、「{“キー”、”値”}」というように、キーと値がセットになった形式となっている。

①キーは必ずダブルクォーテーション（””）で囲む。

```
{“Prefecture” : “Hyogo”}
```

②キーと値の組み合わせが複数ある場合は、カンマで区切る。  

```
{“Prefecture” : “Hyogo”, “Capital” : “Kobe”},
```

③入れ子のように複数のJSONデータを組み合わせることもできる。

```
{“Prefecture” : “Hyogo”, “Capital” : “Kobe”,  

“Information” : {“Population” : 153.7, “Gourmet” : “beef”}},
```

④配列を扱う場合は{}ではなく[]を使用する。配列とは、同じ型のデータを一列に並べたもの。

```
{“Prefecture” : “Hyogo”, “Capital” : “Kobe”,  

“Population Ratio: [0.526, 0.474]},
```
**[4]JSONが対応しているデータ型**  

①**文字列型**　→必ずダブルクォーテーションで囲んで使用。漢字やひらがなも使用可。  

②**数値型**　→ ダブルクォーテーションで囲わずに記述する。  

③**bool** → 真（true）か偽（false）いずれかの値をとるデータ型。ダブルクォーテーションで囲わずに記述する。  

④**null** → 「何もない」という意味。該当する値がない時に使用。  

> 参照：[PARK datemix](https://datamix.co.jp/media/datascience/introduction-to-json/)

## ◎JSONを使用したデータ表現

```
{
   "product":"mayonnaise",
   "maker":"kewpie",
   "price":"520yen",
   "contents":"450g",
   "BestBefore":"12months",
   "nutrition facts":{
      "energy":"100kcal",
      "protein":"0.4g",
      "lipid":"11.2g",
      "carbohydrates":"0.1g",
      "sodium chloride equivalent":"0.3g"
   },
   "allergen":[
      "egg",
      "soy",
      "apple"
   ]
}
```
