---
title: "Google Analytics on jekyll"
published: true
---

[Google Analytics](https://analytics.google.com/) を設定してみた。

[add google analytics by officel · Pull Request #10 · officel/officel.github.io](https://github.com/officel/officel.github.io/pull/10/files)
コードを貼るのが一番手っ取り早いよね、ということで。

gtag.jsのコードはアナリティクスページの管理－プロパティ－トラッキング情報－トラッキングコードに表示されているものを
jekyll に合わせて_config.yamlからトラッキングIDを取得するようにしただけ。

全ページに出力し、再利用する予定がないので _includes/footer.html に直接書いた。

デプロイされたのを確認した数秒後にはカウントが表示されるようになっててしみじみgoogleはすげぇなって。
