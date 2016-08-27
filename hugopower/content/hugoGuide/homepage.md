+++
groups = ["guide"]
title = "homepage"
weight = 1
+++

__________________________________________________________________________________________________________

index.html Template 

This content template is used for spf13.com.

It makes use of partial templates and uses a similar approach as a List.

<!DOCTYPE html>
<html class="no-js" lang="en-US" prefix="og: http://ogp.me/ns# fb: http://ogp.me/ns/fb#">
<head>
    <meta charset="utf-8">

    {{ partial "meta.html" . }}

    <base href="{{ .Site.BaseUrl }}">
    <title>{{ .Site.Title }}</title>
    <link rel="canonical" href="{{ .Permalink }}">
    <link href="{{ .RSSlink }}" rel="alternate" type="application/rss+xml" title="{{ .Site.Title }}" />

    {{ partial "head_includes.html" . }}
</head>
<body lang="en">

{{ partial "subheader.html" . }}

<section id="main">
  <div>
    {{ range first 10 .Data.Pages }}
        {{ .Render "summary"}}
    {{ end }}
  </div>
</section>

{{ partial "footer.html" }}

__________________________________________________________________________________________________________



