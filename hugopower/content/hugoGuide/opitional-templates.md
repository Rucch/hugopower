+++
groups = ["guide"]
title = "opitional templates"
weight = 5
+++
_________________________________________________________________________________________________________
OPITIONAL:

Partial Templates
__
example header.html

this header template is used for spf13.com:

<!doctype html>
<html class="no-js" lang="en-us" prefix="og: http://ogp.me/ns# fb: http://ogp.me/ns/fb#">
<head>
    <meta charset="utf-8">

    {{ partial "meta.html" . }}

    <base href="{{ .site.baseurl }}">
    <title> {{ .title }} : spf13.com </title>
    <link rel="canonical" href="{{ .permalink }}">
    {{ if .rsslink }}<link href="{{ .rsslink }}" rel="alternate" type="application/rss+xml" title="{{ .title }}" />{{ end }}

    {{ partial "head_includes.html" . }}
</head>
<body lang="en">

__
example footer.html

this footer template is used for spf13.com:

<footer>
  <div>
    <p>
    &copy; 2013-14 steve francia.
    <a href="http://creativecommons.org/licenses/by/3.0/" title="creative commons attribution">some rights reserved</a>; 
    please attribute properly and link back. hosted by <a href="http://servergrove.com">servergrove</a>.
    </p>
  </div>
</footer>
<script type="text/javascript">

  var _gaq = _gaq || [];
  _gaq.push(['_setaccount', 'ua-xysyxysy-x']);
  _gaq.push(['_trackpageview']);

  (function() {
    var ga = document.createelement('script');
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 
        'http://www') + '.google-analytics.com/ga.js';
    ga.setattribute('async', 'true');
    document.documentelement.firstchild.appendchild(ga);
  })();

</script>
</body>
</html>

for examples of referencing these templates, see single content templates, list templates and homepage templates.

________________________________________________________________________________________________________
404.html
__
This is a basic example of a 404.html template:

{{ partial "header.html" . }}
{{ partial "subheader.html" . }}

<section id="main">
  <div>
   <h1 id="title">{{ .Title }}</h1>
  </div>
</section>

{{ partial "footer.html" }}

_________________________________________________________________________________________________________
Sitemap.xml
_
This template respects the version 0.9 of the Sitemap Protocol.

<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  {{ range .Data.Pages }}
  <url>
    <loc>{{ .Permalink }}</loc>
    <lastmod>{{ safeHtml ( .Date.Format "2006-01-02T15:04:05-07:00" ) }}</lastmod>{{ with .Sitemap.ChangeFreq }}
    <changefreq>{{ . }}</changefreq>{{ end }}{{ if ge .Sitemap.Priority 0.0 }}
    <priority>{{ .Sitemap.Priority }}</priority>{{ end }}
  </url>
  {{ end }}
</urlset>

Important: Hugo will automatically add the following header line to this file on render…please don’t include this in the template as it’s not valid HTML.

<?xml version="1.0" encoding="utf-8" standalone="yes" ?>
_________________________________________________________________________________________________________

________________________________________________________________________________________________________
The Embedded rss.xml
__
This is the RSS template that ships with Hugo. It adheres to the ATOM 2.0 Spec.

<rss version="2.0" xmlns:atom="http://www.w3.org/2005/Atom">
  <channel>
      <title>{{ .Title }} on {{ .Site.Title }} </title>
      <generator uri="https://gohugo.io">Hugo</generator>
    <link>{{ .Permalink }}</link>
    {{ with .Site.LanguageCode }}<language>{{.}}</language>{{end}}
    {{ with .Site.Author.name }}<author>{{.}}</author>{{end}}
    {{ with .Site.Copyright }}<copyright>{{.}}</copyright>{{end}}
    <updated>{{ .Date.Format "Mon, 02 Jan 2006 15:04:05 MST" }}</updated>
    {{ range first 15 .Data.Pages }}
    <item>
      <title>{{ .Title }}</title>
      <link>{{ .Permalink }}</link>
      <pubDate>{{ .Date.Format "Mon, 02 Jan 2006 15:04:05 MST" }}</pubDate>
      {{with .Site.Author.name}}<author>{{.}}</author>{{end}}
      <guid>{{ .Permalink }}</guid>
      <description>{{ .Content | html }}</description>
    </item>
    {{ end }}
  </channel>
</rss>

Important: Hugo will automatically add the following header line to this file on render… please don’t include this in the template as it’s not valid HTML.

<?xml version="1.0" encoding="utf-8" standalone="yes" ?>
_
