---
title: "Nested `<optgroup>`s are no longer allowed"
date: "2015-10-30T15:02:00-07:00"
categories: ["html", "dom"]
tags: []
versions: ["44"]
references:
    "https://bugzilla.mozilla.org/show_bug.cgi?id=1214164": "Bug 1214164 - Only <options> that are children of <select> or children of <optgroup> children of <select> should be honored"
---
According to the HTML5 spec, nested [`<optgroup>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/optgroup) elements are not valid. Firefox now obeys the spec, so an [`<option>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/option) element put under programatically nested `<optgroup>` elements is no longer a member of the topmost [`<select>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select) element. That means the `<option>` cannot be selected and it won't appear in the `options` DOM property of the `<select>`.