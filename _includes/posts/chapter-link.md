{% assign page = site.pages
  | where: "type", "chapter"
  | where: "book.series", link.series
  | where: "book.number", link.volume_number
  | where: "chapter", link.chapter
  | first %}

[{{ page.title }}]({{ page.url | absolute_url }}){:.btn .btn-block .btn-primary .btn-lg}
