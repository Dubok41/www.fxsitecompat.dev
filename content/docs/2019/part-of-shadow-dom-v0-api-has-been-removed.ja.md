---
title: "Shadow DOM v0 API の一部が削除されました"
date: "2019-05-12T22:11:00-04:00"
categories: ["dom"]
tags: []
versions: ["67"]
references:
    - url: "https://bugzilla.mozilla.org/show_bug.cgi?id=1535438"
      title: "Bug 1535438 - Remove Shadow DOM v0 APIs"
    - url: "https://groups.google.com/d/topic/mozilla.dev.platform/zFwps4VTiXw/discussion"
      title: "Intent to unship: Some Shadow DOM v0 APIs"
---
Firefox 67 で、`getElementsByTagName`、`getElementsByTagNameNS`、`getElementsByClassName` メソッドが `ShadowRoot` インターフェイスから削除されました。これらは、廃止予定となっている Shadow DOM v0 API の一部であり、Firefox 63 で Shadow DOM v1 が使用可能となった際に誤って露呈されてしまったものでした。

`ShadowRoot` は `DocumentFragment` を継承していることから、`querySelector`、`querySelectorAll`、`getElementById` メソッドを代わりに使うことができます。
