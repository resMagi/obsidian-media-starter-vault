---

cssclasses:

- full-width
- media-dashboard

---

- [[#📋 Watchlist|📋 Watchlist]]
- [[#⭐ Top Rated|⭐ Top Rated]]


## 📋 Watchlist

```dataviewjs
// ── Wrapper ───────────────────────────────────────────────────────
const wrapper = dv.container.createEl("div", { cls: "media-wrapper" })
wrapper.style.width = "100%"

// ── Helpers ───────────────────────────────────────────────────────
const isWatched   = p => p.watched && p.watched !== "" && p.watched !== false
const isUnwatched = p => !isWatched(p)
const isRead      = p => p.read && p.read !== "" && p.read !== false
const isUnread    = p => !isRead(p)

const movies = dv.pages('"Media DB/movies"')
const series = dv.pages('"Media DB/series"')
const books  = dv.pages('"Media DB/books"')

// ── Stats row ─────────────────────────────────────────────────────
const statsEl = wrapper.createEl("div", { cls: "media-stats-wrap" })
for (const s of [
  { icon: "🎬", label: "Movies", done: movies.filter(isWatched).length, total: movies.length },
  { icon: "📺", label: "Series", done: series.filter(isWatched).length, total: series.length },
  { icon: "📚", label: "Books",  done: books.filter(isRead).length,      total: books.length  },
]) {
  const pill = statsEl.createEl("div", { cls: "media-stat-pill" })
  pill.innerHTML = `${s.icon} <strong>${s.done}</strong> watched · <strong>${s.total - s.done}</strong> to go · ${s.label}`
}

// ── Shared helpers ────────────────────────────────────────────────
function renderCard(container, p, emoji, ratingProp = "onlineRating", ratingIcon = "★") {
  const card = container.createEl("a", {
    cls: "media-card-row",
    attr: { "data-href": p.file.path, href: p.file.path }
  })
  if (p.image) {
    card.createEl("img", {
      cls: "media-card-row-img",
      attr: { src: p.image, alt: p.title ?? "", loading: "lazy" }
    })
  } else {
    const ph = card.createEl("div", { cls: "media-card-row-img media-card-row-img--placeholder" })
    ph.textContent = emoji
  }
  const info = card.createEl("div", { cls: "media-card-row-info" })
  info.createEl("div", { cls: "media-card-row-title", text: p.title ?? p.file.name })
  info.createEl("div", {
    cls: "media-card-row-meta",
    text: [p.year, p[ratingProp] ? `${ratingIcon} ${p[ratingProp]}` : null].filter(Boolean).join(" · ")
  })
}

function attachShowMore(btn, listEl, sorted, emoji, ratingProp, ratingIcon, initialCount = 5) {
  let showingAll = false
  btn.style.display = sorted.length <= initialCount ? "none" : "block"

  btn.addEventListener("click", () => {
    if (!showingAll) {
      for (const p of sorted.slice(initialCount)) renderCard(listEl, p, emoji, ratingProp, ratingIcon)
      btn.textContent = "Show less"
      showingAll = true
    } else {
      listEl.empty()
      for (const p of sorted.slice(0, initialCount)) renderCard(listEl, p, emoji, ratingProp, ratingIcon)
      btn.textContent = "Show all"
      showingAll = false
    }
  })
}

function getGenres(pages) {
  const set = new Set()
  for (const p of pages) {
    const g = p.genres ?? p.genre ?? []
    const arr = Array.isArray(g) ? g : [g]
    for (const genre of arr)
      if (genre && typeof genre === "string") set.add(genre.trim())
  }
  return [...set].sort()
}

// ── Watchlist column ──────────────────────────────────────────────
function renderColumn(container, emoji, label, allPages, watchedFilter, unwatchedFilter) {
  const col = container.createEl("div", { cls: "media-col" })

  const header = col.createEl("div", { cls: "media-col-header" })
  header.innerHTML = `<span>${emoji}</span><span>${label}</span><span class="media-col-count">${allPages.filter(watchedFilter).length} / ${allPages.length}</span>`

  const genres = getGenres(allPages.filter(unwatchedFilter))
  const selectWrap = col.createEl("div", { cls: "media-col-select-wrap" })
  const select = selectWrap.createEl("select", { cls: "media-col-select" })
  select.createEl("option", { value: "", text: "All genres" })
  for (const g of genres) select.createEl("option", { value: g, text: g })

  const listEl = col.createEl("div", { cls: "media-col-list" })
  const btn = col.createEl("button", { cls: "media-load-more", text: "Show all" })
  let currentSorted = []

  function renderList(genre) {
    listEl.empty()
    btn.textContent = "Show all"

    let pages = allPages.filter(unwatchedFilter)
    if (genre) {
      pages = pages.filter(p => {
        const g = p.genres ?? p.genre ?? []
        const arr = Array.isArray(g) ? g : [g]
        return arr.some(x => x && x.trim().toLowerCase() === genre.toLowerCase())
      })
    }

    currentSorted = pages.sort(p => p.onlineRating ?? 0, "desc").array()

    if (currentSorted.length === 0) {
      listEl.createEl("div", { cls: "media-col-empty", text: "Nothing here yet." })
      btn.style.display = "none"
      return
    }

    for (const p of currentSorted.slice(0, 5)) renderCard(listEl, p, emoji)
    attachShowMore(btn, listEl, currentSorted, emoji, "onlineRating", "★")
  }

  renderList("")
  select.addEventListener("change", () => renderList(select.value))
}

// ── Render ────────────────────────────────────────────────────────
const grid = wrapper.createEl("div", { cls: "media-main-grid" })
renderColumn(grid, "🎬", "Movies", movies, isWatched, isUnwatched)
renderColumn(grid, "📺", "Series", series, isWatched, isUnwatched)
renderColumn(grid, "📚", "Books",  books,  isRead,    isUnread)
```

## ⭐ Top Rated

```dataviewjs
// ── Wrapper ───────────────────────────────────────────────────────
const wrapper = dv.container.createEl("div", { cls: "media-wrapper" })
wrapper.style.width = "100%"

// ── Helpers ───────────────────────────────────────────────────────
const isWatched = p => p.watched && p.watched !== "" && p.watched !== false
const isRead    = p => p.read && p.read !== "" && p.read !== false

const movies = dv.pages('"Media DB/movies"')
const series = dv.pages('"Media DB/series"')
const books  = dv.pages('"Media DB/books"')

// ── Shared helpers ────────────────────────────────────────────────
function renderCard(container, p, emoji, ratingProp = "personalRating", ratingIcon = "⭐") {
  const card = container.createEl("a", {
    cls: "media-card-row",
    attr: { "data-href": p.file.path, href: p.file.path }
  })
  if (p.image) {
    card.createEl("img", {
      cls: "media-card-row-img",
      attr: { src: p.image, alt: p.title ?? "", loading: "lazy" }
    })
  } else {
    const ph = card.createEl("div", { cls: "media-card-row-img media-card-row-img--placeholder" })
    ph.textContent = emoji
  }
  const info = card.createEl("div", { cls: "media-card-row-info" })
  info.createEl("div", { cls: "media-card-row-title", text: p.title ?? p.file.name })
  info.createEl("div", {
    cls: "media-card-row-meta",
    text: [p.year, p[ratingProp] ? `${ratingIcon} ${p[ratingProp]}` : null].filter(Boolean).join(" · ")
  })
}

function attachShowMore(btn, listEl, sorted, emoji, initialCount = 5) {
  let showingAll = false
  btn.style.display = sorted.length <= initialCount ? "none" : "block"

  btn.addEventListener("click", () => {
    if (!showingAll) {
      for (const p of sorted.slice(initialCount)) renderCard(listEl, p, emoji)
      btn.textContent = "Show less"
      showingAll = true
    } else {
      listEl.empty()
      for (const p of sorted.slice(0, initialCount)) renderCard(listEl, p, emoji)
      btn.textContent = "Show more"
      showingAll = false
    }
  })
}

// ── Rated column ──────────────────────────────────────────────────
function renderRatedColumn(container, emoji, label, allPages, watchedFilter) {
  const sorted = allPages
    .filter(watchedFilter)
    .filter(p => p.personalRating != null && p.personalRating !== "")
    .sort(p => p.personalRating ?? 0, "desc")
    .array()

  if (sorted.length === 0) return

  const col = container.createEl("div", { cls: "media-col" })

  const header = col.createEl("div", { cls: "media-col-header" })
  header.innerHTML = `<span>${emoji}</span><span>${label}</span><span class="media-col-count">${sorted.length} rated</span>`

  const listEl = col.createEl("div", { cls: "media-col-list" })
  for (const p of sorted.slice(0, 5)) renderCard(listEl, p, emoji)

  const btn = col.createEl("button", { cls: "media-load-more", text: "Show more" })
  attachShowMore(btn, listEl, sorted, emoji)
}

// ── Render ────────────────────────────────────────────────────────
const grid = wrapper.createEl("div", { cls: "media-main-grid" })
renderRatedColumn(grid, "🎬", "Movies", movies, isWatched)
renderRatedColumn(grid, "📺", "Series", series, isWatched)
renderRatedColumn(grid, "📚", "Books",  books,  isRead)
```