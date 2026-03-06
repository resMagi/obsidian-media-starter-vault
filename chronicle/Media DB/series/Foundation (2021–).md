---

type: series
subType: ""
title: Foundation
englishTitle: Foundation
year: 2021–
dataSource: OMDbAPI
url: https://www.imdb.com/title/tt0804484/
id: tt0804484
plot: A complex saga of humans scattered on planets throughout the galaxy all living under the rule of the Galactic Empire.
genres:
  - Drama
  - Sci-Fi
writer:
  - David S. Goyer
  - Josh Friedman
studio: []
episodes: 0
duration: N/A
onlineRating: 7.6
actors:
  - Jared Harris
  - Lou Llobell
  - Lee Pace
image: https://m.media-amazon.com/images/M/MV5BMzY5OGJhYzItNGQyOS00NmU3LWFhOWMtNGY1OGVlNTlmYjc0XkEyXkFqcGc@._V1_SX300.jpg
released: true
streamingServices: []
airing: false
airedFrom: 09-24-02021
airedTo: unknown
watched: false
lastWatched: ""
personalRating: 0
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