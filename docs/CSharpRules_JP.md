# C#開発のルール (CSharpRules_JP)

## 0. 本規約で使用されている略称

| 略称  | 意味                |
|:------|:--------------------|
| Ex.   | 例です              |
| Ref.  | 参考資料です        |
| Note. | 参考情報です        |

## 1. 本規約について

　このルールは，基本的に開発での命名ルールなどをまとめたものです。

　細かい点については，自身のルールに作りかえて利用していただければ嬉しく思います。

## 2. C#コーディング関係のガイドラインについて

　Microsoft社がMSDNで基本的なC#のコーディング規約などを公開しています。

　本ルールは，これらをベースに記載していますので，ご一読ください。

* Ref. [C#のコーディング規則 (C# プログラミング ガイド)][link1]

* Ref. [名前に関するガイドライン][link2]

* Ref. [C# プログラムの一般構造 (C# プログラミング ガイド)][link3]

* Ref. [メンバーのデザインのガイドライン][link4]

## 3. 基本的なルール

### 3.1. Private フィールド, パラメータ(引数), 変数

Privateなフィールドや，メソッドのパラメータ(引数)，メソッド内の変数などは，Camel形式で命名します。

```cs
// Privateなフィールド
private string fUserId;

// メソッドのパラメータ
public void SampleMethod(string userName) {

  // メソッド内の変数
  string message;

}
```

### 3.2. 名前空間，クラス，プロパティ, メソッド, イベント

名前空間やクラス，プロパティ，メソッド，イベントは，Pascal形式で命名します。

```cs
// 名前空間
namespace SystemName.WinForms {

  // クラス
  public class LoginPage {

    // プロパティ
    public string UserId { get; set; }

    // メソッド
    public Login() {
      return;
    }

    // イベント
    public event EventHandler LoginCompleted();

  }

}
```

### 3.3. コントロール名, イベントハンドラメソッド

WinFormなどでデザイナに貼り付けるコントロールや，イベントを紐づけているメソッドは，Pascal形式で命名します。

```cs
// コントロール
protected TextBox UserNameEdit;

// イベントハンドラメソッド
private void UserNameEdit_Enter(object sender, System.EventArgs e) {
  return;
}
```

* Note.
  * Visual Studioでは，イベントハンドラメソッドを自動生成することができます。
  * 自動生成されるイベントハンドラメソッドは，「(コントロール名)_(イベント名)」の形式で名前が自動的に付けられるため，ここでは，3.2.を満たすためにPascal形式で名前を付けています。

## 4. 命名の規則

### 4.1. クラス

クラスと言っても，実にいろいろな要素がありますが，基本的にはPascal形式で命名します。

また，名前には名詞，名詞句，形容詞句を使用します。

下表のクラスについては，適切なサフィックス(接尾辞)，プレフィックス(接頭辞)を付けます。

| 要素                 | 規則                   | Ex.                    |
|:---------------------|:-----------------------|:-----------------------|
| 例外クラス           | ...Exception           | ArgumentNullException  |
| テストクラス         | ...Test                | EmployeeTest           |
| コレクションクラス   | ...Collection          | EmployeeCollection     |
| 属性クラス           | ...Attribute           | DisplayAttribute       |
| 抽象クラス 　　　    | Abstract...            | AbstractCompany        |
| 例外クラス 　　　    | (Event名) + EventArgs  | MouseClickEventArgs    |

### 4.2. インターフェース

インターフェース(インターフェイス)は，Pascal形式で命名します。

また，名前には，名詞，名詞句，形容詞句を使用します。

下表のインターフェースについては，適切なサフィックス(接尾辞)，プレフィックス(接頭辞)を付けます。

| 要素                        | 規則      | Ex.          |
|:----------------------------|:----------|:-------------|
| インターフェース            | I...      | IGroup       |
| 能力付与型インターフェース  | I...able  | IDisposable  |

### 4.3. メソッド

メソッドは，Pascal形式で命名します。

また，名前には，動詞もしくは動詞句を使用します。

下表のメソッドについては，適切なサフィックス(接尾辞)，プレフィックス(接頭辞)を付けます。

| 要素                  | 規則                     | Ex.                 |
|:----------------------|:-------------------------|:--------------------|
 |戻り値がBool型        | Is + 形容詞              | IsEdited            |
|                       | Can + 動詞               | CanEditable         |
|                       | Has + 名詞               | HasError            |
| ファクトリーメソッド  | Create + オブジェクト名  | ToString            |
| 初期化                | Initialize + 初期化名    | InitializeProperty  |
|                       | Init + 初期化名          | InitEventHandler    |

### 4.4. プロパティ

プロパティは，Pascal形式で命名します。

また，名前には，名詞，名詞句，形容詞を使用します。

下表のプロパティについては，適切なサフィックス(接尾辞)，プレフィックス(接頭辞)を付けます。

| 要素    | 規則          | Ex.          |
|:--------|:--------------|:-------------|
| Bool型  | Is + 形容詞   | IsEdited     |
|         | Can + 動詞    | CanEditable  |
|         | Allow + 名詞  | AllowEdit    |
| Enum型  | 名詞 + Mode   | EditMode     |
|         | 名詞 + Type   | UserType     |

### 4.5. イベント

イベントは，Pascal形式で命名します。

また，名前には，動詞，動詞句を使用します。

```cs
// イベント
public event MouseEventHandler MouseClick;
```

### 4.6. フィールド

フィールドは，PrivateならCamel形式，Private以外ならPascal形式を使用します。

また，名前には，名詞, 名詞句, 形容詞を使用します。

```cs
// privateのフィールド
private string fUserName;

// private以外のフィールド
public string UserName;
```

### 4.7. イベントハンドラ

イベントハンドラは，Pascal形式で命名します。

また，名前には「EventHandler」をサフィックス(接尾辞)にします。

```cs
// イベントハンドラ
public delegate void MouseClickEventHandler(object sender, MouseEventArgs e);
```

### 4.8. 列挙型

列挙型は，Pascal形式で命名します。

また，例外を除いてサフィックス(接尾辞)はつけません。

```cs
public class Teams {

  // 列挙型
  public enum TeamType {
    ENL,
    RES,
    RAY
  }

}
```

### 4.9. コントロール名

コントロール名は，Pascal形式で命名します。

下表は，主なコントロールのサフィックス(接尾辞)です。

| 要素      | Ex.                     |
|:----------|:------------------------|
| Button系  | OkButton, CancelButton  |
| Editor系  | NameEdit, StartDateEdit |
| Label系   | TitleLabel, NameLabel   |

## 5. コーディング時に意識すること

### 5.1. １メソッドあたり３０行以内におさめる

1メソッドあたりの行数は，30行以内におさまるように目指します。

30行を超える場合は，以下を参考におさまるようリファクタリングを行います。

ただし，``Switch``を使用している場合は例外です。

### 5.2. １メソッドは１機能のみ

1つのメソッドに複数の機能を持たせると，再利用性が低くなる原因となります。

たとえば，行追加のメソッド(``AddRow``)内で，行追加と保存の処理を行うなどです。

この場合，行追加と保存の処理は異なるメソッドに分けておき，それぞれを呼び出します。

### 5.3. 不要なコードは削除する

ソースコードをTeamFoundationServerやGitなどで適切に管理している場合，不要なソースコードやコメントは削除すべきです。

不要なソースコードやコメントは，可読性を低くする原因となります。

### 5.4. ネスト構造は浅くする

ネスト構造は浅くするべきです。

もし，深くなってしまう場合には，複数のメソッドに分けるなど，メソッドの再設計を検討します。

ネスト構造が深くなると，可読性が低くする原因となります。

```cs
if ( val1 == 1 ) {
　if ( val2 == 2 ) {
　　if ( val3 == 3 ) {
　　　Method1();
　　}
　　Method2();
　}
　Method3();
}
```

### 5.5. アクセス権は厳格に

アクセス権は，できる限り厳格に設定します。

アクセス権を厳格にしておくことで，外部のクラスなどから不要な項目が見えなくなります。

これにより，意図しない外部からのメソッドの呼び出しや値の変更などを防ぐことができます。

また，VisualStudioなどを使用した際に，目的のプロパティやメソッドなどを早く見つけることが可能となります。

### 5.6. if, for, usingなどの { } は基本省略する

if文やfor文などで使用する { } は，基本的に省略するようにします。

```cs
if ( val == null ) return null;
```

### 5.7. ビジネスロジックは別プロジェクトで

ビジネスロジックは，常に同じ動作をすることが求められます。

そのため，基本的には別プロジェクトで作成しておき，そのプロジェクトを参照してロジックを実行するようにします。

各々のプロジェクトで独自実装を行うことは，改修時に無用な混乱を招く恐れがあります。

### 5.8. イベントハンドラの設定はロジック内で

イベントハンドラの設定は，初期化メソッド(``InitializeEventHandler``など)にまとめてコードを書いておくことをおすすめします。

そうすることで，イベントハンドラの設定が完了しているかを確認することができます。

### 5.9. イベントハンドラメソッド内ではメソッドの呼び出しのみ行う

イベントハンドラメソッド内では処理を行わず，処理が定義されているメソッドを呼び出すようにします。

そうすることで複数のイベントハンドラメソッドでの機能の重複を防ぎ，再利用性を高めることができます。

### 5.10. ログなどで文字列を結合する場合には，StringBuilderを使う

ログなど，既存の文字列の後ろに文字列を追加していく場合，``string``同士を``+``では結合せず，``System.Text.StringBuilder``の``Append``メソッドなどを用いて結合します。

## 6. コード メトリックスとコード分析を行う

### 6.1. コード メトリックス

コード メトリックスを行うと，保守容易性インデックスなどの確認を行うことができます。

チェックイン(コミット)前に，必ず実行して数値の確認を行います。

これらの値が，注意閾値を下回らないように気をつけて実装を行うことで，一定の水準を満たす実装を行うことができます。

### 6.2. コード分析

コード分析もコード メトリックスと同様に行います。

コード分析では，あらかじめ決められたルールに基づいて，実装の注意点などを分析，警告を行います。

警告が無くなるように実装することで，一定のルールに従った実装を行うことができます。

## ライセンス

This documents are licensed under [CC4][linkLisenceEn].

この文章は，[クリエイティブ・コモンズ 表示 4.0 国際 ライセンス][linkLisenceJa]の下に提供されています。

[![CC4][linkLicenseImg]][linkLisenceJa]

[link1]: https://docs.microsoft.com/ja-jp/dotnet/csharp/programming-guide/inside-a-program/coding-conventions "C#のコーディング規則 (C# プログラミング ガイド"
[link2]: https://msdn.microsoft.com/ja-jp/library/ms229002(v=vs.110).aspx "名前に関するガイドライン"
[link3]: https://docs.microsoft.com/ja-jp/dotnet/csharp/programming-guide/inside-a-program/general-structure-of-a-csharp-program "C# プログラムの一般構造 (C# プログラミング ガイド)"
[link4]: https://msdn.microsoft.com/ja-jp/library/ms229059(v=vs.110).aspx "メンバーのデザインのガイドライン"
[linkLisenceEn]: http://creativecommons.org/licenses/by/4.0/ "CC4"
[linkLisenceJa]: http://creativecommons.org/licenses/by/4.0/deed.ja "CC4"
[linkLicenseImg]: https://i.creativecommons.org/l/by/4.0/88x31.png "CC4"