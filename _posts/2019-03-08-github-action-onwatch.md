---
title: "Github Actions on watch"
published: true
---

[GitHub Actions | GitHub Developer Guide](https://developer.github.com/actions/)で遊んでいて、
（まだ自分には来てなくて、同僚のリポジトリを借りてる）
watch event を試してみたのでメモ。

{% raw %}
```
workflow "watch" {
  on = "watch"
  resolves = ["GitHub Action for Slack"]
}

action "GitHub Action for Slack" {
  uses = "Ilshidur/action-slack@88b36649f596e200db270dc72728c6b3ac8bc5bd"
  args = "Action called : {{ GITHUB_ACTION }}"
  env = {
    SLACK_CHANNEL = "githubactionlog"
  }
  secrets = ["SLACK_WEBHOOK"]
}
```
{% endraw %}


`on = "watch"` で [watch](https://developer.github.com/v3/activity/events/types/#watchevent) イベントが拾える。

watch イベントは概要にあるとおり、watch を拾うのではなくて、starred を拾う。リポジトリの右肩にある★のやつ。

actions の slack はビジュアルエディタから [Ilshidur/action-slack: 🚀 GitHub Action that sends a Slack notification.](https://github.com/Ilshidur/action-slack)
を使用した。

マーケットプレイスからは今は落としてある（？）ようで、リンクが死んでるし、マケプレで検索しても出てこないのはなんでだろう？

ヘルプにあるとおりに設定したが、app が Incoming Webhook なのが少し気になるところ。

とはいえスターを付けると発火して無事にslackに投稿されるのを確認した。

イベントのヘルプにあるとおり、スターを *付けた* 時に発火するので、スターを外した時には発火しない。ただしまた付けると発火する。
スターをつけたユーザを区別しないので、スターを付けて外して付けてとするとそれなりに発火するようだ。

リポジトリの通知を付けておけば教えてもらえるので役に立つわけではないが、actionsを勉強するのにはちょうどいい感じだった、という感想。
