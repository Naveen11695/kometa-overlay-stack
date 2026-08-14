# jhn322 Flat Names ↔ overlays/ Tree Mapping

Production Kometa config (from [jhn322/kometa-config](https://github.com/jhn322/kometa-config)) references overlay files as flat names at the `config/` root, e.g. `file: config/3-media_info.yml`. This repo organizes the same YAML into an `overlays/` tree for clarity.

Both layouts are equivalent — choose one and use consistent paths in `config.yml`.

## Path conventions

| Style | Example in config.yml | File on disk |
|-------|----------------------|--------------|
| **Production (flat)** | `file: config/3-media_info.yml` | `kometa/config/3-media_info.yml` |
| **Repo tree** | `file: overlays/movies/media_info.yml` | `kometa/config/overlays/movies/media_info.yml` |

> **Note:** Production `config.yml` uses the `config/` prefix (jhn322 convention). When using the repo tree layout, omit the `config/` prefix or adjust to `overlays/...` paths.

## Active overlays (production)

### Movies

| Production path | Repo path | Description |
|-----------------|-----------|-------------|
| `config/3-media_info.yml` | `overlays/movies/media_info.yml` | jmxd media-info bar (codec, resolution, edition) |
| `config/umtk/UMTK_MOVIES_UPCOMING_OVERLAYS.yml` | `umtk/overlays/UMTK_MOVIES_UPCOMING_OVERLAYS.yml` | Coming Soon movie overlays (UMTK generated) |
| `config/umtk/UMTK_MOVIES_TOP10_OVERLAYS.yml` | `umtk/overlays/UMTK_MOVIES_TOP10_OVERLAYS.yml` | Trending top-10 movie badges (UMTK generated) |
| `config/3-audience_rating.yml` | `overlays/movies/audience_rating.yml` | Audience score chips |
| `config/recently_added.yml` | `overlays/shared/recently_added.yml` | NEW ribbon |

### Shows

| Production path | Repo path | Description |
|-----------------|-----------|-------------|
| `config/3-media_info_shows.yml` | `overlays/tv/media_info.yml` | jmxd media-info bar (TV) |
| `config/umtk/UMTK_TV_UPCOMING_SHOWS_OVERLAYS.yml` | `umtk/overlays/UMTK_TV_UPCOMING_SHOWS_OVERLAYS.yml` | Coming Soon TV overlays |
| `config/umtk/UMTK_TV_TOP10_OVERLAYS.yml` | `umtk/overlays/UMTK_TV_TOP10_OVERLAYS.yml` | Trending top-10 TV badges |
| `config/umtk/TSSK_TV_*_OVERLAYS.yml` (11 files) | `umtk/overlays/TSSK_TV_*_OVERLAYS.yml` | Status ribbons (RETURNING, ENDED, etc.) |
| `config/TSSK-Kabeb.yml` | `overlays/networks/TSSK-Kabeb.yml` | Streaming network logos |
| `config/3-audience_rating.yml` | `overlays/movies/audience_rating.yml` | Audience score (series level) |
| `config/3-audience_rating_episodes.yml` | `overlays/movies/audience_rating_episodes.yml` | Audience score (episode level) |
| `default: runtimes` | `overlays/shared/runtime.yml` | Episode runtime text overlay |

### Anime

Same as Shows, except:

- No `UMTK_TV_TOP10_OVERLAYS.yml`
- Adds `config/animetafill/anime_overlays.yml` (animetafill generated; no static repo equivalent)

## Optional / inactive overlays

Available in repo but **not wired** in production `config.yml`:

### Movies (`3.1-*`)

| Production path | Repo path |
|-----------------|-----------|
| `config/3.1-Movies_Overlays_4K.yml` | `overlays/movies/4k.yml` |
| `config/3.1-Movies_Overlays_Rating.yml` | `overlays/movies/rating.yml` |
| `config/3.1-Movies_Overlays_Subtitle.yml` | `overlays/movies/subtitle.yml` |
| `config/3.1-Movies_Overlays_Top.yml` | `overlays/movies/top.yml` |

### TV Shows (`7.1-*`)

| Production path | Repo path |
|-----------------|-----------|
| `config/7.1-TV_Overlays_4K.yml` | `overlays/tv/4k.yml` |
| `config/7.1-TV_Overlays_Canceled.yml` | `overlays/tv/canceled.yml` |
| `config/7.1-TV_Overlays_Rating.yml` | `overlays/tv/rating.yml` |
| `config/7.1-TV_Overlays_Top.yml` | `overlays/tv/top.yml` |

### Anime (`1.1-*`)

| Production path | Repo path |
|-----------------|-----------|
| `config/1.1-Anime_Overlays_Resolution.yml` | `overlays/anime/resolution.yml` |
| `config/1.1-Anime_Overlays_Rating.yml` | `overlays/anime/rating.yml` |
| `config/1.1-Anime_Overlays_ContentRating.yml` | `overlays/anime/content_rating.yml` |
| `config/1.1-Anime_Overlays_Top.yml` | `overlays/anime/top.yml` |

### Remux (`5.1-*`)

| Production path | Repo path |
|-----------------|-----------|
| `config/5.1-Remux_Overlays.yml` | `overlays/remux/overlays.yml` |
| `config/5.1-Remux_Overlays_Audio.yml` | `overlays/remux/audio.yml` |
| `config/5.1-Remux_Overlays_Rating.yml` | `overlays/remux/rating.yml` |
| `config/5.1-Remux_Overlays_Top.yml` | `overlays/remux/top.yml` |

## UMTK collections (production)

UMTK also generates 15 collection files (previously missing from published repos):

| Collection file | Paired overlay |
|-----------------|----------------|
| `UMTK_MOVIES_UPCOMING_COLLECTION.yml` | `UMTK_MOVIES_UPCOMING_OVERLAYS.yml` |
| `UMTK_MOVIES_TRENDING_COLLECTION.yml` | `UMTK_MOVIES_TOP10_OVERLAYS.yml` |
| `UMTK_TV_UPCOMING_SHOWS_COLLECTION.yml` | `UMTK_TV_UPCOMING_SHOWS_OVERLAYS.yml` |
| `UMTK_TV_TRENDING_COLLECTION.yml` | `UMTK_TV_TOP10_OVERLAYS.yml` |
| `TSSK_TV_*_COLLECTION.yml` (11 files) | `TSSK_TV_*_OVERLAYS.yml` |

Snapshots: `umtk/collections/` and `umtk/overlays/`

## Deploying flat layout from repo tree

To match production paths without editing `config.yml`:

```bash
cd /volume2/docker/kometa/config

# Flat overlay files (active set)
ln -sf overlays/movies/media_info.yml 3-media_info.yml
ln -sf overlays/tv/media_info.yml 3-media_info_shows.yml
ln -sf overlays/movies/audience_rating.yml 3-audience_rating.yml
ln -sf overlays/movies/audience_rating_episodes.yml 3-audience_rating_episodes.yml
ln -sf overlays/shared/recently_added.yml recently_added.yml
ln -sf overlays/networks/TSSK-Kabeb.yml TSSK-Kabeb.yml

# Image assets
cp -r /path/to/kometa-overlay-stack/assets/. overlays/

# UMTK (or let UMTK container generate live)
cp -r /path/to/kometa-overlay-stack/umtk/overlays/* umtk/
cp -r /path/to/kometa-overlay-stack/umtk/collections/* umtk/
```

Or use `overlays/...` paths directly in `config.yml` and skip symlinks.
