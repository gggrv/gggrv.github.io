---
layout: post
title: "[DEV INFO] Wristsaver"
date: 2022-05-17
categories: [something]
tags: [handwriting, machine learning, python, qt, cv2]
---

Generate handwritten text.

<!--more-->

### About

`UTAU`, but for handwriting ("concatenative voice/handwriting synthesis" from any user-defined audio/image files).

### Benefits

- Create custom <ruby>type<rt>font</rt></ruby> from any handwriting and print documents with it.
- Apply custom hand wavering, misalign straight lines of text for more natural feel.
- Define derivative <ruby>types<rt>fonts</rt></ruby> for **bold**, *italic* and other styles.
- Define entire typesets for easy font switching via manuscript formatting commands.
- Easily label handwriting data, train machine learning algorithms on this labeled data.

At this moment the existing, tangible and usable version of this project is a logical clone of the [UTAU](https://en.wikipedia.org/wiki/Utau) program — meaning, any labeling techniques (for example `CV`, `VCV`, `CVC`, `bre`) are possible to implement. Translated to handwriting, that could be `single letter`, `some syllable`, `whole word`, `whole phrase`, `ligature`.

### Comparison Table

| Q | Wristsaver v5.5 | Wristsaver Append |
| --- | --- | --- |
| Exists? | ✔️ Development completed in 2020 | ❄️ Development frozen |
| Usable? | ✔️ | ❌ |
| Documentation, screenshots, video demos? | ✔️ Documentation<br>✔️ Screenshots<br>✔️ Animated `gif` demo | ❌ |
| Available? | ✔️ [GitHub repository](https://github.com/gggrv/edu_archive_wristsaver_v5.5) (click to open) | ❌ |
| Has GUI? | ➕ Only for metadata editor, haphazard. | ✔️ Intended to be GUI-centric application.<br>❌ [Discarded experimental prototype exists](https://github.com/gggrv/wristsaver_append) (click to open). |
| What documents can it print? | Simple `html`+`css` | 🤔 |
| What labeling techniques are supported? | ✔️ Standalone `single letter`<br>✔️ `single letter` that comes only after specific `previous letters`<br>✔️ `single letter` that has visible connector to any `previous`/`next`/`both` letter | Mix-match of text `tokens` |

### Rationale

In honor of ancient traditions, certain ██████████████ require ██ to produce large amount of handwritten text in abysmally short timespan. Doing so often leads to ██████████, ███████, wrist injuries, damp morale, poor performance. Initially, wristsaver was designed to help alleviate such conditions. The `append` version is a low-priority research interest, since it has no practical value outside of very specific environment.

### Development Status of the `append` version

<iframe class="airtable-embed" src="https://airtable.com/embed/shrL3loO2LIA3xI7w?backgroundColor=grayLight&viewControls=on" frameborder="0" onmousewheel="" width="100%" height="533" style="background: transparent; border: 1px solid #ccc;"></iframe>
