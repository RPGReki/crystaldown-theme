{% assign page = site.pages
  | where: "type", "chapter"
  | where: "book.series", page.link.series
  | where: "book.number", page.link.volume_number
  | where: "chapter", page.link.chapter
  | first %}

[{{ page.title }}]({{ page.url | absolute_url }}){:.btn .btn-block .btn-primary .btn-lg}
