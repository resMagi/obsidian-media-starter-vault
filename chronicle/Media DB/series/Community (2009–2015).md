---
type: series
subType: ""
title: Community
englishTitle: Community
year: 2009–2015
dataSource: OMDbAPI
url: https://www.imdb.com/title/tt1439629/
id: tt1439629
plot: A suspended lawyer is forced to enroll in a community college with an eccentric staff and student body.
genres:
  - Comedy
writer:
  - Dan Harmon
studio: []
episodes: 0
duration: 22 min
onlineRating: 8.5
actors:
  - Joel McHale
  - Danny Pudi
  - Donald Glover
image: https://m.media-amazon.com/images/M/MV5BOGIwYzNmYTktZWExZC00MzAyLTk4NTItODgwZmIyNWZhNDEyXkEyXkFqcGc@._V1_SX300.jpg
released: true
streamingServices: []
airing: false
airedFrom: 09-17-02009
airedTo: unknown
watched: true
lastWatched: ""
personalRating: 9
tags: mediaDB/tv/series
---
`$= '![Image|360](' + dv.current().image + ')'`

  

# `$= dv.current().title`


**Genres**:

```dataviewjs

dv.current().genres.length === 0 ? dv.span(' - none') : dv.list(dv.current().genres)

```

  

```dataviewjs

let text = '';

  

if (!dv.current().released) {

text += '**Not released**\n';

if (dv.current().airedFrom) {

text += 'The series will release on ' + dv.current().release_date + '.';

} else {

text += 'The series is not released yet.';

}

} else if (dv.current().airing) {

text += '**Not finished**\n';

text += 'The series is not fully released yet.';

}

  

if (text) {

dv.paragraph(text);

}

```

  

**Type**: `$= dv.current().type`

**Online Rating**: `$= dv.current().onlineRating`

**Episodes**: `$= dv.current().episodes`

**Duration**: `$= dv.current().duration`

**Aired from**: `$= dv.current().airedFrom`

**Aired until**: `$= dv.current().airedTo`

**Studios**: `$= dv.current().studios.join(', ')`

---
## Review

## Notes