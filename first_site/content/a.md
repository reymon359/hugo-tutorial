---
# This is the Front Matter
title: "A"
date: 2019-07-27T12:30:55+02:00
draft: true
author: "ramon"
tags: ["tag1", "tag2", "tag3"]
categories: ["cat1"]
moods: ["Happy", "Upbeat"]
myVar: "myValue" # Custom variable. To access it, in the template use {{ .Params.myVar }}
---

<!-- Custom Shortcode -->
<!-- {{< myshortcode color="blue" >}} -->
<!-- positional parameter -->
<!-- {{< myshortcode blue >}} -->
<!-- Multiple tags shortcode -->

{{< myshortcode >}}
    This is the text inside the shortcode tags
{{< /myshortcode >}}



<!-- Shortcode for youtube video -->
{{< youtube 2xkNJL4gJ9E >}}



This is a.md