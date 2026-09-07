# Website design

This maintenance reference is excluded from the published site. The canonical implementation is `assets/css/site.css`.

## Direction: Salmon Notebook

A warm orange-salmon surround frames cream paper. The typography takes its cue from Edmund’s default editor face, Iowan Old Style: upright, familiar, and comfortable for sustained reading. Modest headings, fine warm rules, and the existing frog mark give the site character. Content, navigation, section order, and page templates remain unchanged.

## Typography

- Editorial stack: `"Iowan Old Style", "Palatino Linotype", Palatino, Georgia, serif`. Iowan is used where installed; other platforms use the local fallbacks. No proprietary font files are distributed.
- Interface: self-hosted Inter, with system sans-serif fallbacks. Its preload is retained.
- Code and dates: self-hosted Roboto Mono, with system monospace fallbacks.
- Body: `clamp(1.0625rem, 1rem + 0.25vw, 1.1875rem)`, line height `1.7`, article measure capped at `66ch`.
- Headings: weight `700`, line height `1.15`, tracking `-0.025em`.
- Main title: `clamp(2.5rem, 6vw, 4rem)`.
- Home title: `clamp(2.6rem, 7vw, 4.5rem)`, capped at `13ch` on mobile. Above `760px`, remove the cap and use `clamp(2.6rem, 5.2vw, 3.8rem)` so the current name fits on one line. Allow natural wrapping for zoom and alternate font metrics.
- Post title: `clamp(2.25rem, 5.5vw, 3.5rem)`.
- Home introduction: `clamp(1.2rem, 2.4vw, 1.4rem)`, line height `1.6`, capped at `43ch`.
- Body paragraphs have no decorative drop caps. Quotations use upright text at `1.05em`, line height `1.65`, and a `3px` accent rule.

The Newsreader font files remain available in the repository, but this design does not load or preload them.

## Palette

Use semantic CSS tokens in components.

| Token | Light | Dark |
| --- | --- | --- |
| Canvas | `#f2a17d` | `#191612` |
| Surface | `#fff8ec` | `#24201a` |
| Muted surface | `#f7e7d5` | `#332a21` |
| Ink | `#302820` | `#f7ecdb` |
| Muted ink | `#75604d` | `#cbbb9f` |
| Accent / personal-name links | `#984423` | `#f3ab80` |
| Rule | `#d7bba0` | `#66503d` |
| Focus | `#0c5a52` | `#73d1c1` |
| Media | `#f0deca` | `#1c1813` |

Canvas values must stay synchronized in the pre-paint script, runtime theme code, and web manifest. Theme selection continues to follow the operating system unless the reader selects a preference.

## Layout and components

The standard shell remains `960px`; photo essays retain the `1320px` wide shell and existing image arrangements. Main padding is `clamp(3rem, 7vw, 5rem)` vertically and `clamp(1.25rem, 7vw, 5.25rem)` horizontally. The shell, masthead, and section dividers use fine warm rules.

Post indexes retain a `9rem` metadata column and flexible title column. Read next retains its three-column desktop arrangement and existing recommendation behavior. About, portfolio, archive, offline, error, and photo-essay pages keep their established structure.

At `760px` and below, the outer padding disappears, a `6px` canvas-colored top edge remains, the written brand hides, and existing lists and figure layouts stack. At `480px`, header spacing tightens and secondary metadata adapts. Keep article text comfortably sized and let code and tables scroll horizontally.

## Accessibility, performance, and behavior

Preserve semantic landmarks, the skip link, keyboard focus outlines, current-page navigation, meaningful labels, and responsive media. Links remain underlined. Hover behavior has keyboard equivalents. Pages and the masthead remain still on load and navigation. There are no click animations or page-entry animations. Existing reduced-motion handling, Turbo navigation, theme switching, copy controls, and offline support remain in place.

Core reading and navigation must work without JavaScript. Reuse existing assets and avoid additional font downloads, decorative imagery, cards, shadows, or new dependencies. Print continues to remove navigation and page chrome and render a narrow reading column.

## Validation

Run `bundle exec jekyll build --trace` and `git diff --check`. Compare generated content and structure, allowing for existing randomized Read next selections. Inspect desktop and mobile pages and both themes. Verify text contrast on the actual reading surface.

Reference: [Edmund default typography](https://github.com/I7T5/Edmund/blob/main/Sources/EdmundCore/Model/EditorTheme.swift).
