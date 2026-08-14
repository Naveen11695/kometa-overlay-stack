# 🙏 Sources & Credits

Accurate attribution for all projects in this overlay stack.

| Project | Repo | What it provides |
|---------|------|------------------|
| **Kometa** | [Kometa-Team/Kometa](https://github.com/Kometa-Team/Kometa) | Official Kometa application, Docker image, and [wiki](https://kometa.wiki/) |
| **ImageMaid** | [Kometa-Team/ImageMaid](https://github.com/Kometa-Team/ImageMaid) | Plex poster cache cleanup after overlay runs |
| **posterizarr** | [fscorrupt/posterizarr](https://github.com/fscorrupt/posterizarr) | Custom poster/backdrop artwork management |
| **animetafill** | [fscorrupt/AniMetaFill](https://github.com/fscorrupt/AniMetaFill) | Canon/filler/mixed episode overlay YAML generation |
| **jhn322 config** | [jhn322/kometa-config](https://github.com/jhn322/kometa-config) | Base Kometa config structure, collection files, flat overlay naming |
| **jmxd overlays** | [jmxd/Kometa](https://github.com/jmxd/Kometa) | Media-info overlay templates (codec, resolution, edition bar) — [support jmxd](https://buymeacoffee.com/jmxd) |
| **UMTK** | [netplexflix/Upcoming-Movies-TV-Shows-for-Kometa](https://github.com/netplexflix/Upcoming-Movies-TV-Shows-for-Kometa) | Trending top-10, Coming Soon, GRAB TO WATCH; generates `umtk/*.yml` (15 overlays + 15 collections) |
| **TSSK-Kabeb** | [netplexflix/Overlays](https://github.com/netplexflix/Overlays) (`TSSK-Kabeb/`) | Streaming network logos and Kabeb-style trending top-10 badge artwork (movies + TV; remote URLs) |
| **TRaSH Guides** | [trash-guides.info](https://trash-guides.info/Radarr/Radarr-recommended-naming-scheme/#plex) | Recommended Plex file naming for media-info overlays |
| **MDBList** | [mdblist.com](https://mdblist.com/) | Trending list data source for UMTK |
| **Sonarr** | [Sonarr/Sonarr](https://github.com/Sonarr/Sonarr) | TV library management (UMTK, animetafill) |
| **Radarr** | [Radarr/Radarr](https://github.com/Radarr/Radarr) | Movie library management (UMTK) |

## Not used in this stack

| Project | Repo | Why not used |
|---------|------|--------------|
| **netplexflix standalone** | [netplexflix/Overlays](https://github.com/netplexflix/Overlays) Docker container | UMTK manages Kabeb overlays; artwork still comes from the repo via remote URLs |
| **netplexflix folder** | `/docker/netplexflix` | Not deployed; UMTK handles Kabeb overlay generation |
| **quickStartKometa** | [netplexflix/quickStartKometa](https://github.com/netplexflix/quickStartKometa) | Not part of production pipeline |
| **TSSK standalone** | [netplexflix/TV-show-status-for-Kometa](https://github.com/netplexflix/TV-show-status-for-Kometa) | TSSK is integrated into UMTK |

## What's customized vs upstream

| Component | Upstream | Customization |
|-----------|----------|---------------|
| Overlay YAML | jhn322 flat files + jmxd media-info | Reorganized into `overlays/` tree; production uses flat `config/` paths |
| Image assets | jmxd badges, Kabeb trending short variants | Bundled in `assets/`; network logos and UMTK trending badges load from netplexflix/Overlays GitHub raw URLs |
| UMTK output | Generated at runtime | Snapshots committed in `umtk/overlays/` and `umtk/collections/` |
| Anime canon/filler | animetafill (live) | Static `anime/canon_filler.example.yml` fallback snapshot |
| Kometa config | jhn322 base | Library names `Movies`, `Shows`, `Anime`; specific overlay wiring per library |
| Docker paths | Community examples | Synology `/volume2/docker/` layout |

## Deprecated repos

The following repos are superseded by this merged package:

- [Naveen11695/kometa-overlay-configs](https://github.com/Naveen11695/kometa-overlay-configs) — YAML only, wrong docs vs production
- [Naveen11695/kometa-overlay-assets](https://github.com/Naveen11695/kometa-overlay-assets) — assets only, separate clone required
