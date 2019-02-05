---
layout: default
title: Djangoのクラスベースのビューでミックスインを使用する
---

# クラスベースのビューでミックスインを使用する

Django のビルトインのクラスベースビューではたくさんの機能が準備されていますが、個別に使いたい機能もあるかもしれません。
例えば、HTTP レスポンスを生成するテンプレートをレンダリングするビューを記述したいとき、TemplateView は使えない状況もあります。
POST ではテンプレートをレンダリングするだけで、GET のときはまったく異なる処理がしたいときなどです。
この場合、TemplateResponse を直接使えますが、コードが重複する結果となってしまいます。

この理由から、Django は個別の機能を提供する多くの mixin を用意しています。
例えば、テンプレートのレンダリングは TemplateResponseMixin でカプセル化されています。
Django のリファレンスドキュメントは full documentation of all the mixins を含んでいます。


## コンテキストとテンプレートのレスポンス

2 つの中心的な mixin が用意されており、クラスベースビュー内のテンプレートを扱うインターフェースに一貫性を保ちやすくなっています。

### TemplateResponseMixin

`TemplateResponse` を返すビューは `RemplateResponseMixin` が提供する `render_to_response()` を利用できます。

### ContextMixin

テンプレートを描画するのに必要なコンテキストデータを必要とする場合がある。
そういった場合は `ContextMixin` の `get_context_data()` を利用する。
保持しておきたいデータを keyword argument 形式で `get_context_data()` にわたす。
`get_context_data()` はdictionaryを返す。


# 翻訳元

https://docs.djangoproject.com/ja/2.1/topics/class-based-views/mixins/
