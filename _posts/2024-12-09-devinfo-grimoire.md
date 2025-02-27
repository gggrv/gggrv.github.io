---
layout: post
title: "[DEV INFO] Grimoire"
date: 2024-12-09
categories: [something]
tags: [python, qt, neo4j, kedro]
---

Create and use own interconnected metadata for anything.

<!--more-->

### About

`foobar2000`, but not for music.

### Benefits

- Create custom interconnected metadata for anything:
    - Actual folders/files on disk (for an annotated/categorized file explorer, catalog of projects/photos/collections/materials)
    - Weblinks (for web browser bookmarks)
    - Concepts (for a comparative table of research keywords)
    - People (for an address/contact book or social graph)
    - ???
- Rename/move/copy actual folders/files according to this custom metadata.
- Write custom GUIs and parsers to automatically get/modify some of the metadata.

Save all this into **self-hosted** graph database.  
Or save all this into partitioned `.parquet`-like file.  
Easily edit multiple records at the same time.

### Comparison Tables

#### Base

| Q | Demo app "Grimoire" from "Educational Archive Dust v5" | Grimoire Experimental Release | Grimoire |
| --- | --- | --- | --- |
| Exists? | ✔️ Development completed in 2023 | ✔️ Development completed in 2024 | ⌛ Development in progress |
| Purpose | ➖ Overcomplicated toy<br>➕ Practice in  small-scale software project management | ➕ Standalone tool<br>➕ Practice in advanced Qt development | ✔️ Professional tool<br>➕ Practice in modular GUI app architecture |
| Usable? | ✔️ | ✔️ | 🚧 Partially |
| Documentation, screenshots, video demos? | ✔️Documentation<br>✔️Video demos | Click to preview:<br><img src="/assets/2024-12-09-playlists-menu.png" width="20px" alt="Enhanced context menus, table views" /><img src="/assets/2024-12-09-playlist-contents.png" width="20px" alt='Only one "playlist" can be active at a time' /><img src="/assets/2024-12-09-foo-editor.png" width="20px" alt="Enhanced FooEditor with responsive row selector" /><img src="/assets/2024-12-09-file-renamer-preset-editor.png" width="20px" alt="Enhanced FileRenamer with responsive previews; FooEditor multiple datatype delegate showcase" /><img src="/assets/2024-12-09-file-renamer-context-menu.png" width="20px" alt="Enhanced FileRenamer preset management context menu" /><img src="/assets/2024-12-09-file-renamer-done.png" width="20px" alt="Enhanced FileRenamer GUI with detailed reports" /><img src="/assets/2024-12-09-rel-compare.png" width="20px" alt="Arbitrary relationship editor prototype, compare selected nodes" /><img src="/assets/2024-12-09-rel-one.png" width="20px" alt="Arbitrary relationship editor prototype, explore one node" /><img src="/assets/2024-12-09-rel-compare-menu.png" width="20px" alt="Arbitrary relationship editor prototype, menu with available functions" /> | 🚧 |
| Pubilshed? | ✔️ [GitHub repository](https://github.com/gggrv/edu_archive_dust_v5) (click to open) | ❌ | 🤔 Depends on the developer's private framework licensing strategy |
| GUI? | ✔️ PyQt5<br>➖ Fancy CSS (experimental, user-editable)<br>➖ Overcomplicated<br>➖ Not user-friendly | ✔️ PyQt6<br>➖ Overcomplicated<br>➕ User-friendly | ✔️ PyQt6<br>➕ Simplified<br>➕ User-friendly |
| User can define own functionality? | ✔️ Overcomplicated `plugins` architecture<br><sub>User can mod default behavior, yet the process is cumbersome</sub> | ❌ | ✔️ Simplified `python API` + `custom GUI` architecture<br><sub>User is expected to define his own GUIs for any behavior, not covered by default widgets; code is organized into strictly managed catalog of namespaces/endpoints</sub> |

#### Graph database features

The app uses the [Neo4J](https://neo4j.com) database. In this section the word "parameters" means "neo4j node or relationship properties".

| Q | Demo app "Grimoire" from "Educational Archive Dust v5" | Grimoire Experimental Release | Grimoire |
| --- | --- | --- | --- |
| Supported datatypes | ✔️ `String` | ✔️ `Boolean`<br>✔️ `Datetime`<br>✔️ `Float`<br>✔️ `Integer`<br>✔️ `String` | ✔️ `Boolean`<br>✔️ `Datetime`<br>✔️ `Dictionary`<br>✔️ `Float`<br>✔️ `Integer`<br>🤔 `List`<br>✔️ `String` |
| `node` explorer/editor<sup>1</sup> | ✔️ | ✔️ | ↓ Is replaced by ↓ |
| Custom fields explorer/editor<sup>2</sup> | ❌ | ❌ | ✔️ |
| Hardcoded `connections` explorer/editor<sup>3</sup> | ❌ | ❌ | ✔️ |
| Arbitrary `connections` explorer/editor<sup>4</sup> | ❌ | ✔️ | 🤔 |
| GUI database editor | ❌ | ❌ | 🤔 |
| GUI search index editor | ❌ | ❌ | 🤔 |
| GUI like Neo4J graph view | ❌ | ❌ | 🤔 |

Footnotes:
1. Can explore only the complete node, returned by the database: `MATCH ... RETURN n`; can edit its parameters.
2. Can explore any user-defined query, returned by the database; can edit relevant node/relationship parameters (provided the ID is present): ```MATCH ... RETURN n3, n1.path, n2.name, r1.role, COUNT(aaa), [ (m1)-[r2:SOME_REL_TYPE]-(m2) | m2 { `ID(m2)`:ID(m2), .title, .path } ] as i_prochiy_trehetazhniy_mat```.
3. Default or user-created GUI automatically assigns connections when adding a node.
4. User can launch dedicated GUI and manually create/edit/remove any connection or its parameters.

#### Data manipulation features

The app uses parts of the [Kedro](https://kedro.org) framework. In this section the word "parameters" means "kedro node parameters".

| Q | Demo app "Grimoire" from "Educational Archive Dust v5" | Grimoire Experimental Release | Grimoire |
| --- | --- | --- | --- |
| GUI to launch / stop / provide place for user-defined <ruby>inputs<rt>parameters</rt></ruby> and outputs of several `Pipelines` | ❌ | ❌ | ✔️ |
| GUI to define custom runtimes | ❌ | ❌ | ❌ |
| GUI like Kedro-Viz | ❌ | ❌ | ❌ |

#### Partitioned file storage / table editing features

Sometimes it is more convenient to open a table, edit it, save it and forget about it, rather than write nodes to the database.

| Q | Demo app "Grimoire" from "Educational Archive Dust v5" | Grimoire Experimental Release | Grimoire |
| --- | --- | --- | --- |
| Can save to a partitioned file rather than to the database? | ❌ | ❌ | 🤔 |
| Can act as a general file editor (for example allow to edit any `.csv`, `.parquet`, `.xls`, etc)? | ❌ | ❌ | 🤔 |

### Rationale

There is way too much information one needs to manage. Where was it saved? How was it named? What was it for? Write that down into custom metadata, automatically dump associated files somewhere and search for whatever is needed via easy-to-write self-defined GUI catalogs/visualizations.
