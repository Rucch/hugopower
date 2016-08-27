+++
groups = ["guide"]
title = "grouping"
weight = 3
+++


____________________________________________________________________________________________________________________
Grouping Content

Hugo provides some grouping functions for list pages. You can use them to group pages by Section, Date etc.

Here are a variety of different ways you can group the content items in your list templates:
_
Grouping by Page field

{{ range .Data.Pages.GroupBy "Section" }}
<h3>{{ .Key }}</h3>
<ul>
    {{ range .Pages }}
    <li>
    <a href="{{ .Permalink }}">{{ .Title }}</a>
    <div class="meta">{{ .Date.Format "Mon, Jan 2, 2006" }}</div>
    </li>
    {{ end }}
</ul>
{{ end }}
_
Grouping by Page date

{{ range .Data.Pages.GroupByDate "2006-01" }}
<h3>{{ .Key }}</h3>
<ul>
    {{ range .Pages }}
    <li>
    <a href="{{ .Permalink }}">{{ .Title }}</a>
    <div class="meta">{{ .Date.Format "Mon, Jan 2, 2006" }}</div>
    </li>
    {{ end }}
</ul>
{{ end }}
__
Reversing Key Order

The ordering of the groups is performed by keys in alpha-numeric order (A–Z, 1–100) and in reverse chronological order (newest first) for dates.

While these are logical defaults, they are not always the desired order. There are two different syntaxes to change the order, they both work the same way, so it’s really just a matter of preference.
_
Reverse method

{{ range (.Data.Pages.GroupBy "Section").Reverse }}
...

{{ range (.Data.Pages.GroupByDate "2006-01").Reverse }}
...
_
Providing the (alternate) direction

{{ range .Data.Pages.GroupByDate "2006-01" "asc" }}
...

{{ range .Data.Pages.GroupBy "Section" "desc" }}
...
_________________________________________________________________________________________________________


