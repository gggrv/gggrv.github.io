---
layout: post
title: "[DEV INFO] Grimoire"
date: 2024-12-09
categories: [something]
tags: [python, qt, neo4j, kedro]
---

Create and use own interconnected metadata for anything

<!--more-->

### About

`foobar2000`, but not for music.

### Benefits

- Create custom interconnected metadata for *anything*:
    - Actual folders/files on disk (like an annotated/categorized file explorer, catalog of projects/photos/collections/materials)
    - Weblinks (like some web browser bookmarks)
    - Concepts (like a comparative table of some research keywords)
    - People (like an address/contact book or social graph)
    - ???
- Rename/move/copy actual folders/files according to this custom metadata.
- Write custom GUIs and parsers to automatically get/modify some of the metadata.

Save all this into **self-hosted** graph database.  
Or save all this into partitioned `.parquet`-like file.

### Comparison Table

#### Base features

| Q | Demo app "Grimoire" from "Educational Archive Dust v5" | Grimoire Experimental Release | Grimoire |
| --- | --- | --- | --- |
| Exists? | ✔️ Development completed in 2023 | ✔️ Development completed in 2024 | ⌛ Development in progress |
| Purpose | <ul><li>Overcomplicated toy</li><li>Practice in  small-scale software project management</li></ul> | <ul><li>Standalone tool</li><li>Practice in advanced Qt development</li><ul> | </ul><li>Professional tool</li><li>Practice in modular GUI app architecture</li></ul> |
| Usable? | ✔️ | ✔️ | 🚧Partially |
| Documentation, screenshots, video demos? | ✔️Documentation<br>✔️Video demos | Click to preview:<br><img src="/assets/2024-12-09-playlists-menu.png" width="20px" alt="Enhanced context menus, table views" /><img src="/assets/2024-12-09-playlist-contents.png" width="20px" alt='Only one "playlist" can be active at a time' /><img src="/assets/2024-12-09-foo-editor.png" width="20px" alt="Enhanced FooEditor with responsive row selector" /><img src="/assets/2024-12-09-file-renamer-preset-editor.png" width="20px" alt="Enhanced FileRenamer with responsive previews; FooEditor multiple datatype editor showcase" /><img src="/assets/2024-12-09-file-renamer-context-menu.png" width="20px" alt="Enhanced FileRenamer preset management context menu" /><img src="/assets/2024-12-09-file-renamer-done.png" width="20px" alt="Enhanced FileRenamer GUI with detailed reports" /><img src="/assets/2024-12-09-rel-compare.png" width="20px" alt="Arbitrary relationship editor prototype, compare selected nodes" /><img src="/assets/2024-12-09-rel-one.png" width="20px" alt="Arbitrary relationship editor prototype, explore one node" /> | 🚧 |
| GitHub repository | ✔️[Click to open](https://github.com/gggrv/edu_archive_dust_v5) | n/a | 🤔Depends on my private framework licensing strategy |
| GUI? | <ul><li>✔️PyQt5</li><li>Fancy CSS (experimental, user-editable)</li><li>❌Overcomplicated</li><li>❌Not user-friendly</li></ul> | <ul><li>✔️PyQt6</li><li>❌Overcomplicated</li><li>✔️User-friendly</li></ul> | <ul><li>✔️PyQt6</li><li>✔️Simplified</li><li>✔️User-friendly</li></ul> |
| User can define own functionality? | ✔️Overcomplicated `plugins` architecture<br><sub>User can mod default behavior, yet the process is cumbersome</sub> | ❌ | ✔️Simplified `python API` + `custom GUI` architecture<br><sub>User is expected to define his own GUIs for any behavior, not covered by default widgets; code is organized into strictly managed catalog of namespaces/endpoints</sub> |

#### Graph database features

The app uses the [Neo4J](https://neo4j.com) database.

| Q | Demo app "Grimoire" from "Educational Archive Dust v5" | Grimoire Experimental Release | Grimoire |
| --- | --- | --- | --- |
| `node` explorer<sup>1</sup> | ✔️ | ✔️ | 🤔 |
| Custom fields explorer<sup>2</sup> | ❌ | ❌ | ✔️ |
| Hardcoded `connections`<sup>3</sup> | ❌ | ❌ | ✔️ |
| Arbitrary `connections`<sup>4</sup> | ❌ | ✔️ | 🤔 |
| GUI database editor | ❌ | ❌ | 🤔 |
| GUI search index editor | ❌ | ❌ | 🤔 |
| GUI like Neo4J graph view | ❌ | ❌ | 🤔 |

Footnotes:
1. Can explore only the complete node, returned by the database: `MATCH ... RETURN n`.
2. Can explore any user-defined query, returned by the database: `MATCH ... RETURN n.path, m2.name, r.role, COUNT(aaa)`.
3. Default or user-created GUI automatically assigns connections when adding a node.
4. User can launch dedicated GUI and manually create/edit/remove any connection.

#### Data manipulation features

The app uses parts of the [Kedro](https://kedro.org) framework.

| Q | Demo app "Grimoire" from "Educational Archive Dust v5" | Grimoire Experimental Release | Grimoire |
| --- | --- | --- | --- |
| GUI to launch / stop / provide place for output of several `Pipelines` | ❌ | ❌ | ✔️ |
| GUI to define custom runtimes | ❌ | ❌ | ❌ |
| GUI like Kedro-Viz | ❌ | ❌ | ❌ |

#### Partitioned file storage features

Sometimes it is more convenient to open a table, edit it, save it and forget about it, rather then write nodes to the database.

| Q | Demo app "Grimoire" from "Educational Archive Dust v5" | Grimoire Experimental Release | Grimoire |
| --- | --- | --- | --- |
| Can save to a file rather then to the database? | ❌ | ❌ | 🤔 |

### Rationale

There is way too much information one needs to manage. Where was it saved? How was it named? What was it for? Write that down into custom metadata, automatically dump associated files somewhere and search for whatever is needed via easy-to-write self-defined GUI catalogs/visualizations.
