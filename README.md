# APEX Creative

Design-agency / studio sub-theme for [APEX](https://www.drupal.org/project/apex). Brutalist / editorial-bold homepage with three landing layouts (portfolio case-study, principal bio / profile, service detail). Targets design agencies, creative studios, freelance designers, brand consultants, motion design shops.

## Overview

apex_creative is the catalog's brutalist-bold sub-theme. Per the [APEX Sub-Theme Catalog](../../docs/planning/APEX-SUBTHEME-CATALOG.md):

- **Audience**: design agencies, creative studios, freelance designers, brand consultants, motion design shops
- **Visual identity**: Archivo display (large, confident headlines) + Space Mono utility (captions, credits, technical chrome). High-contrast brutalist monochrome (near-black + warm off-white) + acid-lime accent. Full-bleed-by-default; the work is the content.
- **Homepage archetype**: Brutalist / editorial-bold
- **Landing layouts**: portfolio case-study, principal bio / profile, service detail
- **Content emphasis**: case_study (projects), person (principals + key talent), service (capabilities)

## Audience

Sites where designers evaluate other designers. Reference set: Pentagram, Mother, Wieden+Kennedy, Instrument, Active Theory, Locomotive — Awwwards Site of the Year winners 2022-2026 converge on brutalist monochrome + bold accent. Per Pillar 5 of the audience research, **creative agencies are direct apex_builder buyers** — apex_creative is also a sales tool. It must impress designers.

## Visual identity

| Aspect | Choice |
|---|---|
| Display + body font | Archivo (Manrope / Inter Tight / Inter / system fallback) — modern grotesque, free, distinctive |
| Mono utility font | Space Mono (JetBrains Mono / IBM Plex Mono / SF Mono / Menlo / Consolas / DejaVu Sans Mono fallback) — distinctive grotesque-mono with brutalist edge |
| Type scale | H1 clamp(2.5rem, 5vw + 1rem, 5.5rem); hero clamp(3rem, 6vw + 1rem, 7rem); statement-block clamp(2.5rem, 5vw + 1rem, 6rem). All weight 800-900 with -0.04em letter-spacing. |
| Palette | Stone 950 `#0a0a0a` brutalist black + Neutral 600 `#525252` medium gray + Lime 500 `#84cc16` acid-green accent (overridable via `apex_schemes` per project / client palette) |
| Density | Generous; full-bleed-by-default; works are the content |
| Reading measure | 60ch (tight + punchy agency case-study copy) |
| Layout direction | LTR + RTL via logical properties |
| Accessibility | WCAG 2.2 AA baseline. 4px acid-lime focus ring (designers respect bold focus indicators). 48px+ touch targets on uppercase brutalist CTAs. |

## Layouts

### Homepage — Brutalist / editorial-bold

Region map per the catalog:

```
[apex_top_bar — minimal: logo + work + about + contact]
[apex_header — minimal]
[apex_main_navigation — work / about / journal / contact (collapsed by default)]
[apex_hero — apex-creative-statement (large-typography manifesto) + featured-work scroll]
[apex_content — work grid (full-bleed apex-creative-work-card tiles, asymmetric)]
[apex_content_post — capabilities + clients + journal teaser]
[apex_footer — contact + careers + social + studio location]
```

### Landing layouts

| Archetype | Drupal template | Content type |
|---|---|---|
| Portfolio case-study | `node--apex-case-study--full.html.twig` | apex_case_study |
| Principal bio / profile | `node--apex-person--full.html.twig` | apex_person |
| Service detail | `node--apex-service--full.html.twig` | apex_service |

## SDC components

Per the catalog spec — 5 components ship with apex_creative:

- `apex-creative-work-card` — full-bleed project preview with image scaling on hover; aspect-ratio variants (square / landscape / portrait / ultra-wide) drive asymmetric homepage grid composition
- `apex-creative-case-study-hero` — cinematic project intro with full-bleed hero image, oversized project name, mono meta block, scroll-down hint with bouncing arrow (reduced-motion compliant)
- `apex-creative-process-strip` — numbered process steps with mono step numbers + display-sans titles; 1/2/3-column responsive layout
- `apex-creative-credits-block` — agency end-credits with role + name pairs in mono columns; supports linked profile URLs
- `apex-creative-statement` — large-typography manifesto block with optional acid-lime emphasis word + inverted (dark-canvas) variant

Components live in `components/<name>/` per the [sub-theme contract](../../docs/architecture/sub-theme-contract.md#sdc-components-contract).

## Demo content

apex_creative's demo content pack (`content/`) imports ~30 nodes via `drush apex:import-demo apex_creative` (smaller than other sub-themes — quality over quantity in portfolio domain):

| Content type | Count |
|---|---|
| apex_case_study (projects) | 15 |
| apex_person (principals + key talent) | 6 |
| apex_service (capabilities) | 5 |
| apex_article (journal entries) | 4 |

## Installation

```bash
composer require drupal/apex_creative
drush theme:enable apex_creative
drush config:set system.theme default apex_creative
drush cr
```

The sub-theme **automatically enables every APEX module** the parent theme depends on.

To install the demo content pack:

```bash
drush apex:import-demo apex_creative   # Drush command shipped by W5 Phase A scaffolding
```

## Customization

Per the [APEX cascade-layer contract](../../docs/architecture/css-cascade-layers.md):

- **Plain CSS** in this sub-theme beats every `@layer apex.*` rule. Brand assertions (Archivo + Space Mono pair, brutalist palette, square-corner CTA discipline, 4px focus ring) go here.
- **Layered CSS** (`@layer apex.base`, `@layer apex.components`, etc.) opts into a default that admin Live Editor / modules can override.

Agencies typically swap the acid-lime accent per project / client brand via apex_schemes (each case-study can have its own scheme — apex_schemes supports per-content-type schemes via apex_color_rules). The Archivo + Space Mono typography pair is the brand-defining choice; replace cautiously.

## The work-grid asymmetry

The homepage work-grid uses `apex-creative-work-card` aspect-ratio variants (square / landscape / portrait / ultra-wide) to produce the brutalist "asymmetric grid" effect. Mix variants intentionally to break visual rhythm; alternating same-aspect-ratio rows reads as conventional / boring on agency portfolios.

## Dependencies

- Drupal core `^11.1`
- `apex_theme` (parent theme — auto-pulls every APEX module the parent depends on)

## Screenshots

_Pending Phase 5 docs polish per [W2 v1-readiness](../../docs/planning/workstreams/2-apex-v1-readiness.md)._

## Changelog

See [CHANGELOG.md](./CHANGELOG.md).

## Troubleshooting

_Pending Phase 5 docs polish. For now, see [APEX-KNOWLEDGE-BASE.md](../../docs/APEX-KNOWLEDGE-BASE.md) and the [APEX briefing](../../docs/APEX-BRIEFING.md)._

## License

GPL-2.0-or-later. Part of the [APEX](https://www.drupal.org/project/apex) design system. Sub-themes are FREE per the [APEX commercial structure](../../docs/planning/workstreams/INDEX.md#commercial-structure-locked-expanded-2026-04-26).
