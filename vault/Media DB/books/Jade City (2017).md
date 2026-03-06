---

type: book
subType: ""
title: Jade City
englishTitle: Jade City
year: 2017
dataSource: OpenLibraryAPI
url: https://openlibrary.org/works/OL19720196W
id: /works/OL19720196W
author:
  - Fonda Lee
plot: unknown
pages: unknown
image: https://covers.openlibrary.org/b/OLID/OL29584565M-L.jpg
onlineRating: 0
isbn: unknown
isbn13: unknown
released: true
read: false
lastRead: ""
personalRating: 0
tags: mediaDB/book
---
`$= '![Image|360](' + dv.current().image + ')'`



# `$= dv.current().title`
  
  

```dataviewjs

if (!dv.current().released) {

dv.span('**Not released** The book is not yet released.')

}

```

  

**Type**: `$= dv.current().type`

**Online Rating**: `$= dv.current().onlineRating`

**Pages**: `$= dv.current().pages`

**Released**: `$= dv.current().released`

**Author**: `$= dv.current().author`

---
## Review

## Notes