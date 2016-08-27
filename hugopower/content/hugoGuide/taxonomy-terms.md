+++
groups = ["guide"]
title = "taxonomy terms"
weight = 4
+++

________________________________________________________________________________________________________
Taxonomy Terms
__
exemple terms.html file

List pages are of the type “node” and have all the node variables and site variables available to use in the templates.

This content template is used for spf13.com. It makes use of partial templates. The list of indexes templates cannot use a content view as they don’t display the content, but rather information about the content.

This particular template lists all of the Tags used on spf13.com and provides a count for the number of pieces of content tagged with each tag.

.Data.Terms is an map of terms ⇒ [contents]

{{ partial "header.html" . }}
{{ partial "subheader.html" . }}

<section id="main">
  <div>
   <h1 id="title">{{ .Title }}</h1>

   <ul>
   {{ $data := .Data }}
    {{ range $key, $value := .Data.Terms }}
    <li><a href="{{ $data.Plural }}/{{ $key | urlize }}"> {{ $key }} </a> {{ len $value }} </li>
    {{ end }}
   </ul>
  </div>
</section>

{{ partial "footer.html" }}
_
Another example listing the content for each term (ordered by Date)

{{ partial "header.html" . }}
{{ partial "subheader.html" . }}

<section id="main">
  <div>
   <h1 id="title">{{ .Title }}</h1>

    {{ $data := .Data }}
    {{ range $key,$value := .Data.Terms.ByCount }}
    <h2><a href="{{ $data.Plural }}/{{ $value.Name | urlize }}"> {{ $value.Name }} </a> {{ $value.Count }} </h2>
    <ul>
        {{ range $value.Pages.ByDate }}
        <li>
            <a href="{{ .Permalink }}">{{ .Title }}</a>
        </li>
        {{ end }}
    </ul>
    {{ end }}
  </div>
</section>

{{ partial "footer.html" }}
__
Ordering

Hugo can order the meta data in two different ways. It can be ordered by the number of content assigned to that key or alphabetically.
_
example indexes.html file (alphabetical)

{{ partial "header.html" . }}
{{ partial "subheader.html" . }}

<section id="main">
  <div>
   <h1 id="title">{{ .Title }}</h1>
   <ul>
   {{ $data := .Data }}
    {{ range $key, $value := .Data.Terms.Alphabetical }}
    <li><a href="{{ $data.Plural }}/{{ $value.Name | urlize }}"> {{ $value.Name }} </a> {{ $value.Count }} </li>
    {{ end }}
   </ul>
  </div>
</section>
{{ partial "footer.html" }}
_
example indexes.html file (ordered)

{{ partial "header.html" . }}
{{ partial "subheader.html" . }}

<section id="main">
  <div>
   <h1 id="title">{{ .Title }}</h1>
   <ul>
   {{ $data := .Data }}
    {{ range $key, $value := .Data.Terms.ByCount }}
    <li><a href="{{ $data.Plural }}/{{ $value.Name | urlize }}"> {{ $value.Name }} </a> {{ $value.Count }} </li>
    {{ end }}
   </ul>
  </div>
</section>

{{ partial "footer.html" }}

__________________________________________________________________________________________________________

