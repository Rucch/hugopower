+++
groups = ["guide"]
title = "list pages"
weight = 2
+++

_______________________________________________________________________________________________________
Exemple List Template Pages
__
Example section template (post.html)

This content template is used for spf13.com. It makes use of partial templates. All examples use a view called either “li” or “summary” which this example site defined.

{{ partial "header.html" . }}
{{ partial "subheader.html" . }}

<section id="main">
  <div>
   <h1 id="title">{{ .Title }}</h1>
        <ul id="list">
            {{ range .Data.Pages }}
                {{ .Render "li"}}
            {{ end }}
        </ul>
  </div>
</section>

{{ partial "footer.html" }}
__
Example taxonomy template (tag.html)

This content template is used for spf13.com. It makes use of partial templates. All examples use a view called either “li” or “summary” which this example site defined.

{{ partial "header.html" . }}
{{ partial "subheader.html" . }}

<section id="main">
  <div>
   <h1 id="title">{{ .Title }}</h1>
    {{ range .Data.Pages }}
        {{ .Render "summary"}}
    {{ end }}
  </div>
</section>

{{ partial "footer.html" }}
__
Ordering Content

In the case of Hugo each list will render the content based on metadata provided in the front matter. See ordering content for more information.

Here are a variety of different ways you can order the content items in your list templates:
_
Order by Weight -> Date (default)

{{ range .Data.Pages }}
<li>
<a href="{{ .Permalink }}">{{ .Title }}</a>
<div class="meta">{{ .Date.Format "Mon, Jan 2, 2006" }}</div>
</li>
{{ end }}
_
Order by Weight -> Date

{{ range .Data.Pages.ByWeight }}
<li>
<a href="{{ .Permalink }}">{{ .Title }}</a>
<div class="meta">{{ .Date.Format "Mon, Jan 2, 2006" }}</div>
</li>
{{ end }}
_
Order by Date

{{ range .Data.Pages.ByDate }}
<li>
<a href="{{ .Permalink }}">{{ .Title }}</a>
<div class="meta">{{ .Date.Format "Mon, Jan 2, 2006" }}</div>
</li>
{{ end }}
_
Order by Length

{{ range .Data.Pages.ByLength }}
<li>
<a href="{{ .Permalink }}">{{ .Title }}</a>
<div class="meta">{{ .Date.Format "Mon, Jan 2, 2006" }}</div>
</li>
{{ end }}
_
Order by Title

{{ range .Data.Pages.ByTitle }}
<li>
<a href="{{ .Permalink }}">{{ .Title }}</a>
<div class="meta">{{ .Date.Format "Mon, Jan 2, 2006" }}</div>
</li>
{{ end }}
_
Order by LinkTitle

{{ range .Data.Pages.ByLinkTitle }}
<li>
<a href="{{ .Permalink }}">{{ .LinkTitle }}</a>
<div class="meta">{{ .Date.Format "Mon, Jan 2, 2006" }}</div>
</li>
{{ end }}
_
Reverse Order

Can be applied to any of the above. Using Date for an example.

{{ range .Data.Pages.ByDate.Reverse }}
<li>
<a href="{{ .Permalink }}">{{ .Title }}</a>
<div class="meta">{{ .Date.Format "Mon, Jan 2, 2006" }}</div>
</li>
{{ end }}
__



