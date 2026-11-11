# AGENTS.md

## Brand & UI rules (read before any UI work)
- Colors, fonts and logos come from `docs/brand.md` and `tokens/tokens.css`. Never invent new colors.
- Data areas (tables, chips, bars, charts) use ONLY the six ISO 513 colors + neutrals. Brand colors (spark/amber/charcoal) are for chrome only: header, footer, buttons, logo.
- ISO colors are always paired with the letter (P/M/K/N/S/H). Never encode meaning by color alone. Range bars keep the fixed order P→M→K→N→S→H.
- UI font is Pretendard GOV; numeric columns use `font-variant-numeric: tabular-nums`. Do not load the wordmark font on the site.
- The logo is the arena badge only. Use `assets/brand/` SVGs as-is; never redraw. Default (Y3) files on light backgrounds, `-dark` files (red arena, white blades) on dark backgrounds; mono files for 1-color print. Below 48px use `-small`, at or below 24px use `-micro` (never just scale the full mark). The wordmark is edgemat✱ch (`05-wordmark/`).
- Accessibility rules: `docs/accessibility.md`.
