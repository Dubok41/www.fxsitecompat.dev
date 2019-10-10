---
title: "WebRTC サイマルキャスト属性内の `pt=` と `rid=` は非対応となりました"
date: "2019-10-09T23:17:00-04:00"
categories: ["audio-video"]
tags: []
versions: ["71"]
statuses: "affecting"
references:
    - url: "https://bugzilla.mozilla.org/show_bug.cgi?id=1225877"
      title: "Bug 1225877 - Parse latest a=simulcast and a=rid"
    - url: "https://bugzilla.mozilla.org/show_bug.cgi?id=1470568"
      title: "Bug 1470568 - Stop supporting \"rid=\" in simulcast attributes once ESR doesn't serialize it anymore"
    - url: "https://bugzilla.mozilla.org/show_bug.cgi?id=1586423"
      title: "Bug 1586423 - meet.google.com / Google Hangouts doesn't work in Nightly (\"Couldn't start the video call because of an error\")"
---
Firefox 71 で、WebRTC サイマルキャスト属性内の旧式パラメーターである `pt=` と `rid=` がパースされなくなりました。Firefox 68 以降で対応している新形式では RID のみが必要とされており、例えば

```
a=simulcast: send rid=8 recv rid=9
```

は以下のようにしなければなりません。

```
a=simulcast: send 8 recv 9
```

現在、この変更により *Google Hangouts Meet* のビデオ通話が使用できなくなっています。