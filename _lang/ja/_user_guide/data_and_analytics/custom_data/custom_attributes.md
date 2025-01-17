---
nav_title: カスタム属性
article_title: カスタム属性
page_order: 10
page_type: reference
description: "このリファレンス記事では、カスタム属性とそのさまざまなデータ型について説明します。"
search_rank: 1
---

# [![Braze Learning course]({% image_buster /assets/img/bl_icon2.png %})](https://learning.braze.com/custom-events-and-attributes){: style="float:right;width:120px;border:0;" class="noimgborder"}カスタム属性

> カスタム属性とは、ユーザー固有の特徴の集合です。カスタム属性は、ユーザーに関する属性や、アプリケーション内の価値の低いアクションに関する情報を格納するために最適です。 

これらの特徴を Braze に保存すると、オーディエンスセグメントの構成、および Liquid を使用したメッセージングのパーソナライゼーションに使用できます。カスタムイベントとは異なり、カスタム属性の時系列情報は保存されないので、時系列情報に基づくグラフを取得できないことに注意してください。

## カスタム属性の管理

ダッシュボードでカスタム属性の作成および管理を行うには、[**データ設定**] > [**カスタム属性**] に移動します。 

{% alert note %}
[古いナビゲーション]({{site.baseurl}}/navigation)を使用している場合、[**カスタム属性**] は [**設定の管理**] の下にあります。
{% endalert %}

このページから、既存のカスタム属性の表示、管理、作成、または禁止リストへの追加ができます。

カスタム属性は、アクションメニューから個別に禁止リストに追加できるほか、最大 10 個の属性を選択して一括で追加できます。カスタム属性をブロックすると、その属性に関するデータは収集されず、既存のデータは再アクティブ化しない限り利用できなくなります。また、禁止リストに追加された属性はフィルターやグラフに表示されません。さらに、属性が現在 Braze ダッシュボードの他の領域のフィルターまたはトリガーによって参照されている場合、「それを参照するフィルターまたはトリガーのすべてのインスタンスが削除され、アーカイブされる」という内容の警告モーダルが表示されます。

管理者は、このページからカスタム属性を作成して PII としてマークすることもできます。これらの属性は、「PII としてマークされたカスタム属性の表示」権限を持つ管理者とダッシュボードユーザーにのみ表示されます。

ユーザープロファイルからカスタム属性を削除するには、[`/users/track` エンドポイント]({{site.baseurl}}/api/endpoints/user_data/post_user_track#user-track)への API リクエストでその値を「null」に設定します。

## カスタム属性の設定

さまざまなプラットフォームで、カスタム属性の設定に使用する方法を以下に示します。

{% details Expand for documentation by platform %}

- [Android と FireOS]({{site.baseurl}}/developer_guide/platform_integration_guides/android/analytics/setting_custom_attributes/)
- [iOS]({{site.baseurl}}/developer_guide/platform_integration_guides/swift/analytics/setting_custom_attributes/)
- [Web]({{site.baseurl}}/developer_guide/platform_integration_guides/web/analytics/setting_custom_attributes/)
- [React Native]({{site.baseurl}}/developer_guide/platform_integration_guides/react_native/analytics/#logging-custom-attributes)
- [Unity]({{site.baseurl}}/developer_guide/platform_integration_guides/unity/Analytics/setting_custom_attributes/)
- [Xamarin]({{site.baseurl}}/developer_guide/platform_integration_guides/xamarin/analytics/#setting-custom-attributes)
- [Roku]({{site.baseurl}}/developer_guide/platform_integration_guides/roku/analytics/setting_custom_attributes/)

{% enddetails %}

## カスタム属性の保存

カスタム属性データを含めて、**ユーザープロファイル**に保存されているデータはすべて、各プロファイルが[アクティブ]({{site.baseurl}}/user_guide/data_and_analytics/user_data_collection/user_archival/#active-users)である限り、無期限に保持されます。

## カスタム属性のデータ型

カスタム属性は、優れたターゲット設定を可能にする非常に柔軟なツールです。

カスタム属性として格納できるデータ型を以下に示します。

- [ブール値](#booleans)
- [数値](#numbers)
- [文字列](#strings)
- [配列](#arrays)
- [時刻](#time)
- [オブジェクト]({{site.baseurl}}/user_guide/data_and_analytics/custom_data/custom_attributes/nested_custom_attribute_support/)
- [オブジェクトの配列]({{site.baseurl}}/user_guide/data_and_analytics/custom_data/custom_attributes/array_of_objects/)

### ブール値 (true/false) {#booleans}

ブール値を持つ属性は、サブスクリプションステータスなど、ユーザーに関する単純な 2 値データを格納する場合に便利です。その属性のレコードがまだ記録されていないユーザーに加えて、変数が明示的に true または false の値に設定されているユーザーを検出できます。

| セグメンテーションオプション | ドロップダウンフィルター | 入力オプション | 例 |
| ---------------------| --------------- | ------------- | -------- |
| ブール値**が** true、false、true または未設定、あるいは false または未設定のいずれかであるかをチェックする | **が** | [**TRUE**]、[**FALSE**]、[**TRUE または設定なし**]、あるいは [**FALSE または設定なし**] | このフィルターに `coffee_drinker` が指定された場合、以下の状況でユーザーがこのフィルターに一致します。<br> {::nomarkdown}<ul><li>このフィルターが [<code>true</code>] で、かつユーザーが値 <code>coffee\_drinker</code> を持つ。</li><li>このフィルターが [<code>false</code>] で、かつユーザーが値 <code>coffee\_drinker</code> を持たない。</li><li>このフィルターが [<code>true または未設定</code>] で、かつユーザーが値 <code>coffee\_drinker</code> を持つか、値がない。</li><li>このフィルターが [<code>false または未設定</code>] で、かつユーザーが値 <code>coffee\_drinker</code> も他の値も持たない。</li></ul>{:/} |
| ユーザープロファイルにブール値が**存在**してかつ null でないかをチェックする | [**空白でない**] | **なし** | このフィルターに `coffee_drinker` が指定され、ユーザーに属性 `coffee_drinker` の値がある場合、ユーザーはこのフィルターに一致します。 |
| ユーザープロファイルにブール値が**存在しない**、または null であるかをチェックする | [**が空白**] | **なし** | このフィルターに `coffee_drinker` が指定され、ユーザーに属性 `coffee_drinker` がないか、`coffee_drinker` の値が null の場合、ユーザーはこのフィルターに一致します。|
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3 .reset-td-br-4}

### 数値 {#numbers}

数値属性には[整数](https://en.wikipedia.org/wiki/Integer)や[浮動小数点](https://en.wikipedia.org/wiki/Floating-point_arithmetic)などがあり、さまざまなユースケースがあります。数値のカスタム属性を増分すると、特定のアクションやイベントが発生した回数を、データキャップにカウントせずに保存する場合に便利です。標準数には、以下の記録など、あらゆる用途があります。

- 靴のサイズ
- ウェストサイズ
- ユーザーが特定の製品機能またはカテゴリを表示した回数

{% alert tip %}
支出した金額はこの方法で記録すべきではありません。むしろ、[購入方法](#purchase-revenue-tracking)で記録すべきです。
{% endalert %}

| セグメンテーションオプション | ドロップダウンフィルター | 入力オプション | 例 |
| ---------------------| --------------- | ------------- | -------- |
| 数値属性がある**数値**と**正確に一致**するかをチェックする | [**正確に一致**] | **数値** | このフィルターに `10` が指定され、ユーザープロファイルに値 `10` がある場合、ユーザーはこのフィルターに一致します。 |
| 数値属性が**数値**と**等しくない**かをチェックする | [**等しくない**] | **数値** | このフィルターに `10` が指定され、ユーザープロファイルに値 `10` がない場合、ユーザーはこのフィルターに一致します。 |
| 数値属性がある**数値****より大きい**かをチェックする | [**超**] | **数値** | このフィルターに `10` が指定され、ユーザープロファイルの値が `10` より大きい場合、ユーザーはこのフィルターに一致します。|
| 数値属性がある**数値****より小さい**かをチェックする | [**未満**] |**数値** | このフィルターに `10` が指定され、ユーザープロファイルの値が `10` より小さい場合、ユーザーはこのフィルターに一致します。 |
| 数値属性がユーザープロファイルに**存在**して、かつ null でないかをチェックする | [**空白でない**] | **なし** | 指定した数値属性がユーザープロファイルに含まれている場合、値に関係なく、ユーザーはこのフィルターに一致します。 |
| 数値属性がユーザーのプロファイルに**存在しない**か、または null かをチェックする | [**が空白**] | **なし** | 指定した数値属性がユーザープロファイルに含まれていないか、属性値が null の場合、ユーザーはこのフィルターに一致します。|
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3 .reset-td-br-4}

#### 数値属性の詳細

- 「正確に 0」と「未満」のフィルターは NULL フィールドを持つユーザーを含みます。
  - カスタム属性の値を持たないユーザーを除外するには、[**空白でない**] フィルターを含める必要があります。

### 文字列 (英数字) {#strings}

文字列属性は、お気に入りのブランド、電話番号、アプリケーション内での最後の検索文字列など、ユーザー入力の保存に役立ちます。文字列属性の長さは最大 255 文字です。

単語の間、前後、または後にスペースを含む値を入力すると、Braze はそのスペースもチェックすることに注意してください。

| セグメンテーションオプション | ドロップダウンフィルター | 入力オプション | 例 |
| ---------------------| --------------- | ------------- | -------- |
| 文字列属性が入力された文字列と**完全一致**するかをチェックする | [**等しい**] |**文字列**<br>大文字小文字を区別する | このフィルターに `book` が指定され、ユーザープロファイルに `book` を含む `last_item_purchased` の文字列属性がある場合、ユーザーはこのフィルターに一致します。|
| 文字列属性が、入力された文字列**または**正規表現に**部分一致**するかをチェックする | [**正規表現に一致する**] |**文字列****または****正規表現**<br>大文字小文字は区別されず、最大 32,764 文字です。 |
| 文字列属性が、入力された文字列**または**正規表現に**部分一致しない**かをチェックする | [**正規表現に一致しない**]* |**文字列****または****正規表現**<br>大文字小文字を区別せず、最大 32,764 文字 |
| 入力された文字列と文字列属性が**一致しない**かをチェックする | [**等しくない**] | **文字列**<br>大文字小文字を区別しない  | このフィルターに `book` が指定され、ユーザープロファイルにある `last_item_purchased` の文字列属性が `book` を含まない場合、ユーザーはこのフィルターに一致します。|
| 文字列属性がユーザーのプロファイルに**存在**して、かつ空の文字列でないかをチェックする | [**空白でない**] | **なし** | このフィルターに `favorite_genre` が指定され、ユーザープロファイルに属性 `favorite_genre` がある場合、ユーザーは属性値に関係なくこのフィルターに一致します。例えば、ユーザーは `sci-fi`、`romance`、または他の値を持つことができます。|
| ユーザープロファイルに文字列属性**が存在しない**かをチェックする | [**空白**] | **なし** | このフィルターに `favorite_genre` が指定され、ユーザープロファイルに属性 `favorite_genre` がない場合、ユーザーはこのフィルターに一致します。|
| 入力された文字列の**いずれか**に完全一致するかをチェックする| [**いずれか**] | **文字列**<br>大文字小文字を区別し、複数の文字列を使用可能 (最大 256 個) | このフィルターに `book`、`bookmark`、および `reading light` が指定され、ユーザープロファイルにこれらの文字列の少なくとも 1 つがある場合、ユーザーはこのフィルタに一致します。|
| 文字列属性が、入力された文字列の**いずれとも完全一致**しないかをチェックする | [**いずれでもない**] |**文字列**<br>大文字小文字を区別し、複数の文字列を使用可能 (最大 256 個) | このフィルターに `book`、`bookmark`、および `reading light` が指定され、ユーザープロファイルにこれらの文字列がいずれも含まれていない場合、ユーザーはフィルターに一致します。|
| 文字列属性が、入力された文字列の**いずれかと部分一致**するかをチェックする | [**いずれかを含む**] | **文字列**<br>大文字小文字を区別し、複数の文字列を使用可能 (最大 256 個) | このフィルターに `gold` が指定され、ユーザープロファイルのいずれかの文字列に `gold` が含まれている場合 (`gold_tier` や `former_gold_tier` など)、ユーザーはフィルタに一致します。|
| 文字列属性が、入力されたどの文字列にも**部分一致しない**かをチェックする | [**いずれも含まない**] | **文字列**<br>大文字小文字を区別し、複数の文字列を使用可能 (最大 256 個) | このフィルターに `gold` が指定され、ユーザープロファイルにどの文字列にも `gold` が含まれていない場合、ユーザーはこのフィルタに一致します。|
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3 .reset-td-br-4}

{% alert note %}
「12-1-2021」、「12/1/2021" will be converted to a datetime object and treated as a [時刻属性]({{site.baseurl}}/user_guide/data_and_analytics/custom_data/custom_attributes/#time)。
{% endalert %}

{% alert important %}
[**正規表現に一致しない**] フィルターを使用してセグメント化する場合、そのユーザープロファイルに、値を持つカスタム属性がすでに存在している必要があります。ターゲットがユーザーに適切に設定されていることを確認するために、「または」ロジックを使用してカスタム属性が空白であるかどうかチェックすることをお勧めします。<br>

正規表現に関するその他のリソース:
- [Braze での正規表現]({{site.baseurl}}/user_guide/engagement_tools/segments/regex/)
- [正規表現のデバッガーおよびテスター](https://regex101.com/)
- [正規表現のチュートリアル (英語版)](https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285)
{% endalert %}

### 配列 {#arrays}

配列属性は、ユーザーに関する情報の関連リストの保存に適しています。例えば、ユーザーが視聴した最後のコンテンツ 100 個を配列内に保存すると、特定の関心に基づくセグメンテーションができます。

属性の配列の最大長は、デフォルトで 25 に設定されており、個々の配列について 100 に増やすことができます。例えば、「視聴した映画」のような属性を渡していて、配列長が 100 に設定されている場合、ユーザーが 101 本目の映画を視聴すると、配列から最初の映画が削除され、最新の映画が追加されます。

この最大値を増やしたい場合は、カスタマーサクセスマネージャーにお問い合わせください。ダッシュボード管理者は、[**設定の管理**] ページの [**カスタム属性**] タブから、個々の配列の最大長を 100 より大きくすることができます。

単語の間、前後、または後にスペースを含む値を入力すると、Braze はそのスペースもチェックすることに注意してください。

{% alert note %}
属性がデータ型を自動的に検出するように設定されている場合、最大長を増やすオプションは使用できません。データ型を配列に設定する必要があります。
{% endalert %}

| セグメンテーションオプション | ドロップダウンフィルター | 入力オプション | 例 |
| ---------------------| --------------- | ------------- | -------- |
| 配列属性が、入力された値と**正確に一致する値を含む**かをチェックする| [**値を含む**] | **文字列** | このフィルターに `sci-fi` が指定され、ユーザープロファイルに値 `sci-fi` がある場合、ユーザーはこのフィルターに一致します。|
| 配列属性が、入力された値と**正確に一致する値を含まない**かをチェックする| [**値を含まない**] | **文字列** | このフィルターに `sci-fi` が指定され、ユーザープロファイルに値 `sci-fi` がない場合、ユーザーはこのフィルターに一致します。|
| 配列属性が、入力された値**または**正規表現と**部分一致する値を含む**かをチェックする | [**正規表現に一致する**] | **文字列****または****正規表現**<br>最大 32,764 文字 | |
| 配列属性が**値を持つ**か空でないことをチェックする | [**値を持つ**] | **なし** | このフィルターに `favorite_genres` が指定され、ユーザープロファイルに任意の値を持つ `favorite_genres` が含まれている場合、ユーザーはこのフィルターに一致します。 |
| 配列属性が**空**か存在しないことをチェックする | [**空である**] | **なし** | このフィルターに `favorite_genres` が指定され、ユーザープロファイルに `favorite_genres` がないか、`favorite_genres` はあるが値がない場合、ユーザーはこのフィルターに一致します。|
| 配列属性が、入力された値の**いずれかに完全一致する値を含む**かをチェックする | [**いずれかを含む**] | **文字列**<br>大文字小文字を区別し、複数の値を使用可能 (最大 256 個) | このフィルターに `sci-fi, fantasy, romance` が指定され、ユーザープロファイルに `sci-fi`、`fantasy`、`romance` の任意の組み合わせがある場合 (`sci-fi` のみなど、1 つのみの場合も含む)。`sci-fi`、`fantasy`、`romance` のいずれかがある場合、文字列に `horror` や他の値があってもかまいません。|
| 配列属性が、入力された値の**いずれにも完全一致する値を含まない**かをチェックする | [**いずれも含まない**] | **文字列**<br>大文字小文字を区別し、複数の値を使用可能 (最大 256 個) | このフィルターに `sci-fi, fantasy, romance`が指定され、ユーザープロファイルに `sci-fi`、`fantasy`、`romance` のいずれの組み合わせも含まれていない場合、ユーザーはこのフィルターに一致します。`sci-fi`、`fantasy`、`romance` のいずれもない場合、`horror` や他の値があってもかまいません。|
| 配列属性が、入力された値の**いずれかに部分一致する値を含む**かをチェックする | [**値がいずれかを含む**] | **文字列**<br>大文字小文字を区別し、複数の値を使用可能 (最大 256 個) | このフィルターに `gold` が指定され、ユーザープロファイルの配列の少なくとも 1 つの文字列に `gold` がある場合、ユーザーはこのフィルターに一致します。`gold_tier`、`former_gold_tier` などの文字列値が該当します。|
| 配列属性が、入力された値の**いずれかに部分一致する値を含まない**かをチェックする | [**値がいずれもを含まない] | **文字列**<br>大文字小文字を区別し、複数の値を使用可能 (最大 256 個) | このフィルターに `gold` が指定され、ユーザープロファイルの配列のいずれの文字列にも `gold` が含まれていない場合、ユーザーはこのフィルターに一致します。つまり、`gold_tier` や `former_gold_tier` のような文字列値を持つユーザーは、このフィルターに一致しません。|
| 配列属性が、入力された値を**すべて含む**かをチェックする | [**すべて含む**] | **文字列**<br>大文字小文字を区別し、複数の値を使用可能 (最大 256 個) | このフィルターに `sci-fi, fantasy, romance` が指定され、ユーザープロファイルにそれらの値がすべて含まれている場合、ユーザーはこのフィルターに一致します。ユーザーに `horror` や他の値があっても、このフィルターに一致します。|
| 配列属性が、入力された値の**いずれかを含まない**かをチェックする | **[すべてではない**] | **文字列**<br>大文字小文字を区別し、複数の値を使用可能 (最大 256 個)| このフィルターに `sci-fi, fantasy, romance` が指定され、ユーザープロファイルにそれらの値がいずれかでも含まれていない場合、ユーザーはこのフィルターに一致します。|
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3 .reset-td-br-4}

{% alert tip %}
正規表現フィルターの使用方法の詳細については、[Perl 対応正規表現](http://www.regextester.com/pregsyntax.html) (PCRE) のドキュメントをご覧ください。
<br>
正規表現に関するその他のリソース:
- [Braze での正規表現]({{site.baseurl}}/user_guide/engagement_tools/segments/regex/)
- [正規表現のデバッガーおよびテスター]({{site.baseurl}}/user_guide/engagement_tools/segments/regex/)
- [正規表現のチュートリアル](https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285)
{% endalert %}

### 時刻 {#time}

時刻属性は、特定のアクションが最後に実行された時刻の保存に役立ちます。そのため、コンテンツ固有の再エンゲージメントメッセージをユーザーに提供できます。

相対日付 (1 日超前、2 日未満など) を使用した時刻フィルターでは、1 日を 24 時間として扱います。これらのフィルターを使用して実行するキャンペーンには、24 時間範囲のすべてのユーザーが含まれます。例えば、`last used app more than 1 day ago` はキャンペーンが実行される正確な時刻から「アプリの最終使用が 24 時間超前」のすべてのユーザーを取得します。より長い日付範囲が設定されているキャンペーンも同様です。つまり、「アクティブ化から 5 日間」は、以前の 120 時間を意味します。

例えば、24 ～ 48 時間後に含まれる時刻属性を持つユーザーを対象にするセグメントを構成するには、フィルター `in more than 1 day in the future` と `in less than 2 days in the future` を適用します。

{% alert warning %}
カスタムイベントまたは購入イベントが最後に発生した日付は自動的に記録されます。カスタム時刻属性を使用して再度記録しないでください。
{% endalert %}

| セグメンテーションオプション | ドロップダウンフィルター | 入力オプション | 例 |
| ---------------------| --------------- | ------------- | -------- |
| 時刻属性が**選択した日付****より前**かをチェックする| [**前**] |**カレンダー日付セレクター** | このフィルターに `2024-01-31` が指定され、ユーザープロファイルに `2024-1-31` より前の日付がある場合、ユーザーはこのフィルターに一致します。|
| 時刻属性が**選択した日****より後**かをチェックする | [**後**] | **カレンダー日付セレクター** | このフィルターに `2024-01-31` を指定し、ユーザープロファイルに `2024-1-31` より後の日付がある場合、ユーザーはこのフィルターに一致します。|
| 時刻属性が **過去 X 日間****より前**かをチェックする | [**超**] | [**過去の日数** | このフィルターに `7` が指定され、ユーザープロファイルの日付が過去 7 日間より前である場合、ユーザーはこのフィルターに一致します。 |
| 時刻属性が**過去 X 日間****以内**かをチェック する| [**未満**] | **過去の日数** | このフィルターに `7` が指定され、ユーザープロファイルの日付が過去 7 日間以内である場合、ユーザーはこのフィルターに一致します。|
| 時刻属性が **未来 X 日間****より後か**をチェックする | [**超**] | [**未来の日数** | このフィルターに `7` が指定され、ユーザープロファイルの日付が未来 7 日間より後である場合、ユーザーはこのフィルターに一致します。 |
| 時刻属性が **未来 X 日間****以内**かをチェックする | [**未満**] | **未来の日数**  | このフィルターに `7` が指定され、ユーザープロファイルの日付が未来 7 日間以内である場合、ユーザーはこのフィルターに一致します。 |
| ユーザープロファイルに時間属性が**存在**してかつ null でないかをチェックする | [**空白でない**] | **なし** | このフィルターに指定された時刻属性がユーザープロファイルにある場合、ユーザーはこのフィルターに一致します。 |
| ユーザープロファイルに時刻属性が**存在しない**か null であることをチェックする | [**空白である**] | **なし** | このフィルターに指定された時刻属性がユーザープロファイルにない場合、ユーザーはこのフィルターに一致します。 |
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3 .reset-td-br-4}

#### 時間属性の詳細

- 定期的なイベントの日
  - [定期的なイベントの日] フィルターを使用し、その後に [定期的なイベントのカレンダー日] を選択するように求められたときに、`IS LESS THAN` または `IS MORE THAN` を選択すると、現在の日付がそのセグメンテーションフィルターでカウントされます。
  - 例えば、2020 年 3 月 10 日に選択した属性の日付が `LESS THAN ... March 10, 2020` である場合、その属性で考慮される日付は 2020 年 3 月 10 日まで (2020 年 3 月10 日を含む) になります。 
- 過去 X 日間以内:「過去 X 日間以内」フィルターには、過去 X 日から現在の日付 / 時刻までの日付が含まれます。
- 未来 X 日間以内: 現在の日付 / 時刻から未来 X 日までの日付が含まれます。

### オブジェクト

階層化カスタム属性を使用して、カスタム属性のデータ型としてオブジェクトを送信できます。詳細については、「[階層化カスタム属性]({{site.baseurl}}/user_guide/data_and_analytics/custom_data/custom_attributes/nested_custom_attribute_support/)」を参照してください。

### オブジェクト配列

関連する属性をグループ化するには、オブジェクト配列を使用します。詳細については、「[オブジェクト配列]({{site.baseurl}}/user_guide/data_and_analytics/custom_data/custom_attributes/array_of_objects/)」の記事を参照してください。

### 演算子の集約

属性フィルター、カスタム属性フィルター、階層化カスタム属性フィルターで使用できる演算子のリストを整理しました。既存のフィルターでこれらの演算子を使用している場合、新しい演算子を使用するように自動的に更新されます。

| データ型 | 古い演算子 | 新しい演算子 | 値 |
| --- | --- | --- | --- |
| 文字列 | 等しい | いずれかである | 少なくとも 1 つの値 |
| 文字列 | 等しくない | いずれでもない | 少なくとも 1 つの値 |
| 配列 | 値を含む | いずれかを含む | 少なくとも 1 つの値 |
| 配列 | 値を含まない | いずれも含まない | 少なくとも 1 つの値 |
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3 .reset-td-br-4}

## 購入と収益の追跡{#purchase-revenue-tracking}

アプリ内購入の記録に弊社の購入方法を使用すると、個々のユーザープロファイルに生涯価値 (LTV) が設定されます。このデータは、弊社の [収益] ページに表示できます。

| セグメンテーションオプション | ドロップダウンフィルター | 入力オプション | 例 |
| ---------------------| --------------- | ------------- | -------- |
| 合計支出金額 (ドル単位) が**数値****より大きい**かをチェックする | [**より大きい**] | **数値** | このフィルターに `500` が指定され、ユーザープロファイルの値が `500` より大きい場合、ユーザーはこのフィルターに一致します。 |
| 合計支出金額 (ドル単位) が**数値****より小さい**かをチェックする| [**より小さい**] | **数値** | このフィルターに `500` が指定され、ユーザープロファイルの値が `500` 未満の場合、ユーザーはこのフィルターに一致します。|
| 合計支出金額 (ドル単位) が**数値**と**正確**に一致するかをチェックする | [**完全一致**] | **数値** | このフィルターに `500` が指定され、ユーザープロファイルに値 `500` がある場合、ユーザーはこのフィルターに一致します。 |
| 最終購入日が**日付 X の後**かをチェックする | [**後**] | **時刻** | このフィルターに `2024/31/1` が指定され、ユーザーの最終購入日が `2024/31/1` より後だった場合、ユーザーはこのフィルターに一致します。|
| 最終購入日が**日付 X より前**かをチェックする | [**前**] | **時刻** | このフィルターに `2024/31/1` が指定され、ユーザーの最終購入日が `2024/31/1` より前の場合、ユーザーはこのフィルターに一致します。|
| 最終購入日が **過去 X 日間より前**かどうかをチェックする | [**より大きい**] | **時刻** | このフィルターに `7` が指定され、ユーザーの最終購入日が今日から過去 7 日間より前である場合、ユーザーはこのフィルターに一致します。|
| 最終購入日が**過去 X 日間以内**かをチェックする | [**より小さい**] | **時刻** | このフィルターに `7` が指定され、ユーザーの最終購入日が今日から過去 7 日間以内である場合、ユーザーはこのフィルターに一致します。|
| 購入回数が **X 回より大きい (X の最大値 =50)** かをチェックする | [**より大きい**] | 過去 **Y 日間 (Y=1,3,7,14,21,30)** | このフィルターに回数 `7` と日数 `21` が指定され、ユーザーの過去 21 日間の購入回数が 7 回より多い場合、ユーザーはこのフィルターに一致します。|
| 購入回数が **X 回未満 (X の最大値 =50)** かをチェックする | [**より小さい**] | 過去 **Y 日間 (Y=1,3,7,14,21,30)** | このフィルターに回数 `7` と 日数 `21`が指定され、ユーザーの過去 21 日間の購入回数が 7 回より少ない場合、ユーザーはこのフィルターに一致します。|
| 購入回数が **正確に X 回 (X の最大値 =50)** かをチェックする | [**完全一致**] | 過去 **Y 日間 (Y=1,3,7,14,21,30)** | このフィルターに回数 `7` と 日数 `21` が指定され、ユーザーの過去 21 日間の購入回数が 7 回の場合、ユーザーはこのフィルターに一致します。|
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3 .reset-td-br-4}

{% alert tip %}
特定の購入の発生回数でセグメンテーションを行う場合は、その購入を個別に[増分カスタム属性]({{site.baseurl}}/developer_guide/platform_integration_guides/swift/analytics/setting_custom_attributes/#incrementingdecrementing-custom-attributes)として記録する必要もあります。
{% endalert %}

カスタム属性のデータ型を変更できますが、[データ型の変更]({{site.baseurl}}/help/help_articles/data/change_custom_data_type/)による影響に注意する必要があります。

