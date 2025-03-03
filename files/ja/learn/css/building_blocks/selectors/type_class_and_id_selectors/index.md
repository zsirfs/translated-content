---
title: 要素・クラス・ID によるセレクター
slug: Learn/CSS/Building_blocks/Selectors/Type_Class_and_ID_Selectors
---
{{LearnSidebar}}{{PreviousMenuNext("Learn/CSS/Building_blocks/Selectors", "Learn/CSS/Building_blocks/Selectors/Attribute_selectors", "Learn/CSS/Building_blocks")}}

このレッスンでは、利用できる最も簡単にみえるセレクタをとりあげます。これは今後あなたが作業でよく使うことになります。

| 前提条件: | 基本的なコンピューターリテラシー、[基本的なソフトウェアがインストールされている](/ja/Learn/Getting_started_with_the_web/Installing_basic_software)こと、[ファイルの扱い](/ja/Learn/Getting_started_with_the_web/Dealing_with_files)、HTML の基本（[HTML 入門](/ja/docs/Learn/HTML/Introduction_to_HTML)）および CSS に関するアイデア（[CSS の第一歩](/ja/docs/Learn/CSS/First_steps)）に関する基本的な知識を得ている。 |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 目的:     | CSS をドキュメントに適用するためのさまざまな CSS セレクタについて学ぶ。                                                                                                                                                                                                                                                                                                                                                |

## タイプセレクタ

**タイプセレクタ**は*タグ名セレクタ*または*要素セレクタ*を参照します。これはあなたのドキュメント中のタグまたは要素を選択するからです。次の例で span, em それに strong セレクタを使用します。そのため `<span>`, `<em>` と `<strong>` の要素はスタイル修飾されます。

**CSS ルールを追加して `<h1>` 要素を選択してその色を青に変えましょう。**

{{EmbedGHLiveSample("css-examples/learn/selectors/type.html", '100%', 1100)}}

## ユニバーサルセレクタ

ユニバーサルセレクタはアステリスク (`*`) で表します。またこれはドキュメントのすべてまたは親要素に含まれるすべての要素( これはそれが連なっている、他の要素やそれらの子要素に連なっている要素すべて) を選択します。次の例ではすべての要素から margin を削除しています。これはブラウザーによって追加されたデフォルトのスタイルの代りに、章立てやパラグラフの margin を消してそれぞれを近く配置させます。これにより個々のパラグラフが見分けがつかなくなってしまいます。

{{EmbedGHLiveSample("css-examples/learn/selectors/universal.html", '100%', 750)}}

この種類の動作はしばしば「スタイルシートのリセット」と呼び、ブラウザーのスタイル設定を取り消します。ユニバーサルセレクタはグローバルな変更をもたらすため、下記に述べる特定の状況のみに使うべきです。

### ユニバーサルセレクタを使用してセレクタの可読性をあげる

ユニバーサルセレクタの使用方法のひとつに、セレクタを読みやすくし、その動作を明かにするのものがあります。例えば、`<article>` 要素の最初の子要素を選択し、それがどんな要素であったとしてもそれを太字にしたいとします。これには{{cssxref(":first-child")}} セレクタを使うことができます。これはあとの[疑似クラスと疑似要素](/ja/docs/Learn/CSS/Building_blocks/Selectors/Pseudo-classes_and_pseudo-elements)のコースで詳細を学びますが、`<article>` 要素セレクタの後ろで指定します。

```css
article :first-child {

}
```

しかしこれは、`article:first-child` と混同しかねません。これは他の要素の第一子要素の`<article>` 要素を選択してしまうのです。

この混乱を避けるために、`:first-child` にユニバーサルセレクタを追加します。これで何を選択しているかが明らかです。`<article>` 要素の第一子要素にあたるすべての要素を選択しています。

```css
article *:first-child {

}
```

## クラスセレクタ

クラスセレクタの名前はピリオド `(.`) から始まります。そしてそのクラスが適用されている、ドキュメント内のすべてを選択します。次の例では、`.highlight` というクラスを作成し、ドキュメントのいくつかの場所に適用します。このクラスが適用されたすべての要素をハイライトします。

{{EmbedGHLiveSample("css-examples/learn/selectors/class.html", '100%', 750)}}

### 特定の要素のクラスを対象にする

特定のクラスが適用された特定の要素を対象にするセレクタを作成できます。次の例では、`highlight` クラスの `<span>` をハイライトしますが、`highlight` クラスの `<h1>` 見出しを異なるようにハイライトします。対象にしたい要素にタイプセレクタを使用して実現できます。ドットの後にクラスを追加しますが、クラスとの間にホワイトスペースをいれません。

{{EmbedGHLiveSample("css-examples/learn/selectors/class-type.html", '100%', 750)}}

このアプローチでは、ルールが特定の要素とクラスの組み合わせにのみ適用されるため、ルールの範囲が狭くなります。そのため、ルールを他の要素にも適用したい場合は、別のセレクタを追加する必要があります。

### 複数のクラスが適用された要素を対象にする

一つの要素に複数のクラスを適用できます。それらを個別に選択することも、すべてのクラスがあるものだけを選択することもできます。これは、サイト上で様々な方法で組み合わせることができるコンポーネントを構築する際に便利です。

次の例は、ノートのある `<div>` です。灰色の境界はそのボックスが `notebox` クラスもっている場合にのみ適用されます。もしそれが `warning` や `danger` クラスも持っていた場合 {{cssxref("border-color")}} を変更します。

ブラウザーに、2 つのクラスが存在する要素だけ一致するように指定するには、それらのクラスをすべて空白を入れずに繋げて指定します。最後の `<div>` には `danger` クラスがあるだけなので、適用されるスタイルはありません。

{{EmbedGHLiveSample("css-examples/learn/selectors/class-many.html", '100%', 900)}}

## ID セレクタ

ID セレクタは ピリオドではなく `#` で始めますが、それ以外は基本的にクラスセレクタと同じです。しかし ID はそのドキュメントの名にはただ一度しか使用できません。ID セレクタはその `id` が設定されている要素を選択します。要素と ID の両方に一致するものだけを対象にする場合、ID セレクタをタイプセレクタの前に置くことができます。これを次の例で確認しましょう。:

{{EmbedGHLiveSample("css-examples/learn/selectors/id.html", '100%', 750)}}

> **Note:** このレッスンの特例で学んだように ID は非常に特別なもので、他のセレクタを上書きすることがあります。これは対応が難しくなることがあります。多くの場合、ID を使用する代りにクラスを追加するほうが望ましいです。しかしその要素を対象にする方法が ID を使うしかないような場合、例えばそのマークアップにあなたがアクセスできず、編集できないような場合、この方法を使用できます。

## 次の記事

[属性セレクタ](/ja/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors) によるセレクタを調べます。

{{PreviousMenuNext("Learn/CSS/Building_blocks/Selectors", "Learn/CSS/Building_blocks/Selectors/Attribute_selectors", "Learn/CSS/Building_blocks")}}

## このモジュール

1. [カスケードと継承](/ja/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance)
2. [CSS セレクタ](/ja/docs/Learn/CSS/Building_blocks/Selectors)

    - [要素・クラス・ID によるセレクタ](/ja/docs/Learn/CSS/Building_blocks/Selectors/Type_Class_and_ID_Selectors)
    - [属性によるセレクタ](/ja/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors)
    - [擬似クラスおよび疑似要素によるセレクタ](/ja/docs/Learn/CSS/Building_blocks/Selectors/Pseudo-classes_and_pseudo-elements)
    - [結合子](/ja/docs/Learn/CSS/Building_blocks/Selectors/Combinators)

3. [ボックスモデル](/ja/docs/Learn/CSS/Building_blocks/The_box_model)
4. [背景と枠線](/ja/docs/Learn/CSS/Building_blocks/Backgrounds_and_borders)
5. [テキスト方向の操作](/ja/docs/Learn/CSS/Building_blocks/Handling_different_text_directions)
6. [要素のはみ出し（オーバーフロー）](/ja/docs/Learn/CSS/Building_blocks/Overflowing_content)
7. [CSS の値と単位](/ja/docs/Learn/CSS/Building_blocks/Values_and_units)
8. [CSS によるサイズ設定](/ja/docs/Learn/CSS/Building_blocks/Sizing_items_in_CSS)
9. [画像・メディア・フォーム要素](/ja/docs/Learn/CSS/Building_blocks/Images_media_form_elements)
10. [表のスタイリング](/ja/docs/Learn/CSS/Building_blocks/Styling_tables)
11. [CSS のデバッグ](/ja/docs/Learn/CSS/Building_blocks/Debugging_CSS)
12. [CSS の整理](/ja/docs/Learn/CSS/Building_blocks/Organizing)
