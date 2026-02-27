---

type: movie
subType: ""
title: Seven Samurai
englishTitle: Seven Samurai
year: "1954"
dataSource: OMDbAPI
url: https://www.imdb.com/title/tt0047478/
id: tt0047478
plot: Farmers from a village exploited by bandits hire a veteran samurai for protection, and he gathers six other samurai to join him.
genres:
  - Action
  - Drama
director:
  - Akira Kurosawa
writer:
  - Akira Kurosawa
  - Shinobu Hashimoto
  - Hideo Oguni
studio:
  - N/A
duration: 207 min
onlineRating: 8.6
actors:
  - Toshirô Mifune
  - Takashi Shimura
  - Keiko Tsushima
image: https://m.media-amazon.com/images/M/MV5BZjliMWExOTMtZDQ3ZS00NWU3LWIyN2EtMjllNzk3ZTNlYzg4XkEyXkFqcGc@._V1_SX300.jpg
released: true
streamingServices: []
premiere: 11-19-01956
watched: false
lastWatched: ""
personalRating: 0
tags: mediaDB/tv/movie
---
`$= '![Image|360](' + dv.current().image + ')'`

  

# `$= dv.current().title`
  

**Genres**:

```dataviewjs

dv.current().genres.length === 0 ? dv.span(' - none') : dv.list(dv.current().genres)

```

  

```dataviewjs

if (!dv.current().released) {

dv.span('**Not released** The movie is not yet released.')

}

```

  

**Type**: `$= dv.current().type`

**Online Rating**: `$= dv.current().onlineRating`

**Duration**: `$= dv.current().duration`

**Premiered**: `$= dv.current().premiere`

**Producer**: `$= dv.current().producer`

---
## Review

## Notes