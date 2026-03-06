# 🎬 obsidian-media-starter-vault

> A focused Obsidian starter vault for tracking your personal media history — films, series, books and more.

[![Reddit](https://img.shields.io/badge/r%2FObsidianMD-discuss-FF4500?style=flat&logo=reddit&logoColor=white)](https://www.reddit.com/r/ObsidianMD)
[![Obsidian Forum](https://img.shields.io/badge/Obsidian%20Forum-discuss-7C3AED?style=flat&logo=obsidian&logoColor=white)](https://forum.obsidian.md)
[![GitHub Release](https://img.shields.io/github/v/release/resMagi/obsidian-media-starter-vault?style=flat&color=4CAF50)](https://github.com/resMagi/obsidian-media-starter-vault/releases)

![Dashboard Screenshot](assets/screenshot-dashboard.png)

---

## Why this vault?

I've tried tracking my media consumption in different ways — OneNote, Letterboxd, Goodreads. They all work, but none of them gave me the flexibility I wanted. I couldn't add my own notes or structure things my way. 
Since I already live in Obsidian, building a media tracker there was the natural next step. When I went looking for a ready-made starter vault I only found tutorials — so after building my own, I decided to share it.
This vault gives you full control over how you track, review and reflect on the media you consume.

---

## Features

- 📥 **One-click media import** via the Media DB plugin — search for a title and it lands in your vault automatically with metadata, poster image and more
- 📋 **Watchlist & read list** — watch, read and history lists displayed via Obsidian Bases
- 📺 **Movies, series and books supported** out of the box
- ✅ **Automatic watched tracking** — mark an item as watched or add a personal rating and it moves to your history automatically
- 🎨 **Custom dashboard** — built with DataviewJS and CSS snippets, showing your watchlist and top rated media at a glance
- ⭐ **Top Rated section** — overview of your highest rated media by personal rating and unwatched media by online rating

---

## Used Plugins

| Plugin | Purpose |
|--------|---------|
| [Media DB](https://github.com/mProjectsCode/obsidian-media-db-plugin) | Fetch media metadata from external APIs |
| [Dataview](https://github.com/blacksmithgu/obsidian-dataview) | Power the dashboard queries |
| [Templater](https://github.com/SilverRainZ/obsidian-templater) | Auto-apply templates on file creation |

---

## Setup

### 1. Fork or clone this repo

Forking is recommended — it lets you pull in future updates while keeping your own changes:

```bash
git clone https://github.com/resMagi/obsidian-media-starter-vault.git
```

### 2. Open as vault in Obsidian

Open Obsidian → **Open folder as vault** → select the `vault` folder inside the repo (you can rename it).

### 3. Enable Community plugins

Go to **Settings → Community plugins → Enable Community plugins**.

The required plugins are already included in the repo — no need to install them manually.

### 4. Enable CSS snippets

Go to **Settings → Appearance → CSS snippets** and enable:
- `full-width`
- `media-dashboard`

### 5. Add your OMDb API key

Go to **Settings → Media DB** and add your OMDb API key for movies and series.
Get a free key at [omdbapi.com](https://www.omdbapi.com/apikey.aspx). Other APIs are optional.

### 6. Start tracking

Use the Media DB plugin — click the ribbon icon or press `Cmd/Ctrl + P` → *Add new Media DB entry* — to search for a title. It will be added to the correct folder automatically with full metadata.

---

## How Watched Tracking Works

> 📸 *GIF coming soon — showing how to mark an item as watched*

When you open a media entry you will find two key properties in the frontmatter:

- **`watched`** — check this checkbox to mark the item as watched
- **`personalRating`** — add a rating (e.g. `8.5`) once you've watched it

Either action will automatically move the entry from your watchlist into your watched history via Obsidian Bases. No manual sorting needed.

---

## Vault Structure

```
obsidian-media-starter-vault/   ← repo root
├── chronicle/                  ← open this as your Obsidian vault
│   ├── .obsidian/
│   │   ├── plugins/            # Community plugins (pre-configured)
│   │   └── snippets/           # CSS snippets (full-width, media-dashboard)
│   ├── Media DB/
│   │   ├── movies/             # One note per movie
│   │   ├── series/             # One note per series
│   │   └── books/              # One note per book
│   ├── _templates/
│   │   ├── movie.md
│   │   ├── series.md
│   │   └── book.md
│   ├── lists/                  # Obsidian Bases views
│   └── dashboard.md            # DataviewJS dashboard
├── .gitignore
├── LICENSE
└── README.md
```

---

## Example Vault

Want to see what a filled vault looks like? Check out [chronicle](https://github.com/resMagi/chronicle) — my personal media vault built on this starter.

---

## Roadmap

- [ ] Manga support
- [ ] Games support
- [ ] GitHub Pages showcase

---

## Contributing & Updates

If you want to pull in future improvements, fork this repo and add it as upstream:

```bash
git remote add upstream https://github.com/resMagi/obsidian-media-starter-vault.git
git pull upstream main
```

Issues and pull requests are welcome.

---

## License

MIT — do whatever you want with it.``
