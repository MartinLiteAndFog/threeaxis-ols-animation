# ThreeAxis / OLS — interactive research animation

Live: https://martinliteandfog.github.io/threeaxis-ols-animation/

Offline-capable, self-contained HTML chart comparing historical Nasdaq ORB, OLS10, XYZ3 and the separate X3/Y3/Z4/XYZ10 sensor filters with the Original 7 portfolio.

- **Capital (default):** actual historical modelled private-account wealth including reinvested, received prop payouts versus identical personal contributions (EUR 1,000 initially, then EUR 100/month Jan 2020 through Dec 2021 = EUR 3,400).
- **Cashflow-neutral strategy return:** separate TWR-style view, never conflated with capital earned using the prop-financing mechanism.
- Each model can be compared with/without its own independently simulated prop account ladder. Solid curves represent prop-funded, dashed curves represent direct private-investment alternatives. Model selector, historical timeline, optional drawdown and SYMLOG axis available.
- 17% protected private cash reserve, hypothetical prop 2% stop risk, private 10% stop risk, 18x notional ceiling, 1.9 index points spread and 0.5 points slippage per fill in the Nasdaq research replays.

**Important:** Historical, retrospectively modelled results, not independently validated forward performance. Prop-firm terms and fills are hypothetical. Original 7 uses a different strategy composition from the individual Nasdaq variants. Nominal prop account balances are **not** counted as owned capital. This repository contains only the standalone visualization, not trading execution code.

## Mobile layout

Optimized for iPhone-sized portrait screens, including 375, 390, and 430 CSS pixel viewports. The interface scrolls vertically, preserves an independent chart and readable KPI cards, provides touch-based chart seeking, a quick jump to the last backtest day, and accessible model/method panels. The line style legend appears when both prop variants are shown.

## Simplified mobile navigation (portrait and landscape)

The chart is the default focus. Time window, prop-financing mode, view, axis style, model visibility and methodology are now hidden by default behind a single **Menü** control on mobile devices in both orientations. Selecting an option closes the popover; outside taps and Escape dismiss it. The animation controls, capital values, line-style legend and time scrub remain accessible without opening the menu. Verified on 390×844 and 844×390 emulated touch displays.

## Cashreserve und Originalformel (27.11.2026)

- **Menü > Reserve:** 0 %, 10 %, 17 %, 20 % und 30 % als eigenständig nachgerechnete geschützte Reserve für jede der acht Strategien. Der bisherige Standard von 17 % bleibt erhalten. Die Auswahl verändert die Kapital- und Renditepfade aller Strategien; es wird keine bestehende 17%-Kurve nur skaliert.
- Geschützte Cashreserve lässt sich als separate Linie zu jeder Strategie einblenden; sie wird als Prozentsatz der identischen eigenen Einzahlungen dargestellt. Der genaue EUR-Betrag und die Quote am Privatvermögen erscheinen darunter. Kein doppeltes Addieren zum Nettovermögen.
- **Menü > Formel:** Originale adaptive Portfolioformel aus `Quant_PropFirm_Portfolio_2020-2026_EN_40_17_Wide.html` mit Variablen-Glossar; standardmäßig verborgen und als Modell des Original-7-/Top-2-Portfolios gekennzeichnet (nicht Gleichung der NQ-OLS-Filter).
- Fehlerkorrektur: Der Original-7-Prop-Endwert für die 17%-Reserve hatte in der früheren Visualisierung die **geschützte Cashreserve von 3.495.998,16 € nicht mitgezählt**. Privates Gesamtvermögen inkl. 540 € verbliebener Prop-Gebührenkasse: **23.993.327,71 €** (statt 20.497.329,55 €). Diese geparkte Reserve ist privates Eigentum, aber nicht handelbar.
- In der Strategierendite- und Drawdown-Ansicht bleibt die Reserve-Linie aus, weil eine Kontostands-Kurve in der TWR-Prozentachse nicht direkt sinnvoll vergleichbar wäre.
- Reproduktion lokal über `research/overnight_orb_indices_20261123/regression_overlay_20261126/causal_3axis_20261127/{replay_reserve_variants_20261127.py,build_reserve_formula_20261127.py}`. Der 17%-Wert reproduziert das bestehende Modell; 0% und 10/20/30% sind neu gerechnet, nicht behauptete Live-Werte.

## Protected cash: correct units and original footer (Nov 27, 2026)

- The optional protected cash balance is plotted using an **independent EUR axis** on the LEFT; its end label and tooltip read **Cash … €**, not a percent of personal contributions. All other wealth/performance series still use the independent right-side % axis.
- The footer permanently shows three live **EUR figures** based on selected arm, funding mode and reserve target: **Private Portfolio** = all actually owned private equity including locked cash, **Protected Cash Reserve** = the locked cash subset, **No Reserve (0%)** = independently simulated alternative with zero protected reserve. The first two MUST NOT be added together.
- The footer includes optional TWR-style maximum drawdowns and, in the 'both' financing view, a smaller no-prop counterfactual. It updates for all 0/10/17/20/30% targets and eight strategy arms, and works during animation.
- **Menu > Reserve:** optional independent 'No Reserve' equity curve, normal percent wealth axis, alongside the cash EUR overlay. The historical prop payout timetable is the same across reserve targets; no live prop-provider claims.
- Reproducible Mac builder: `research/overnight_orb_indices_20261123/regression_overlay_20261126/causal_3axis_20261127/build_euro_cash_footer_20261127.py`. Verified by browser interaction in phone portrait and landscape, and exact model checks (Original7 at 17%: 23,993,327.71 € portfolio, 3,495,998.16 € cash, 40,390,504.71 € unprotected alternative).

## 27 Nov 2026: Common EUR chart and original 7 components

- Default **Kapital** view: **all portfolio, cash-reserve, no-reserve and independently invested market benchmarks use the same actual EUR axis**, not % of contributions. The shared `SYMLOG` (asinh, EUR 1,000 linearization scale) makes both small and very large EUR values visible; `LINEAR` is available too. EUR decade grid labels at left, EUR curve labels at right. No separate misleading cash axis. **Strategierendite** and **Drawdown** retain their own % units, only when explicitly selected.
- Finance mode dropdown remains `Mit / ohne Prop` (solid/dashed) and `Mit Prop` or `Ohne Prop`; for each of the eight portfolio research scenarios we use saved separate private account NAV for the chosen 0/10/17/20/30% reserve target. The footer retains `Private Portfolio`, `Protected Cash Reserve` (a part of the former, not additive), `No Reserve (0%)` in EUR.
- The model chooser displays **Original 7**, **XYZ3** and **Nasdaq-ORB** by default. Optional **Original-7 component single-strategy research curves**: `IMBA TP/SL`, `Kombination`, `Neubau`, `Box`, `Concretum`, `Literatur` and `Nasdaq-ORB10` from 2021-01-01 to 2025-12-31. Redundant OLS10/X/Y/Z/XYZ10 entries are no longer in the model picker. These optional reference series are independently normalized to a hypothetical EUR 1,000 account at 2021-01-01 with cashflow-neutral reinvested single-strategy daily returns; **NOT actual historical contributions, weights or Prop-firm attribution of the Original-7 portfolio**. The 2026-11-11 original strategy selection is retrospective (selection bias). No data extrapolated to 2026.
- Existing independent market reference assets (Nasdaq, ETH, SOL, BTC, S&P 500) also have EUR 1,000 at source inception without external cashflow/Prop, not identical to the portfolio funding schedule.
- `Cloud Science Commodities` is explicitly listed as **not available yet** in the Models panel: an auditable dated commodity strategy NAV history wasn't found on the current research Mac, in MIND or in the accessible Drive project files. No dummy line is drawn.
- Reproducible local scripts: `.../causal_3axis_20261127/{build_euro_original7_components_20261127.py,finalize_euro_original7_20261127.py,polish_euro_original7_20261127.py}`. Browser-tests on 390x844, 844x390 and 1440x900 show no horizontal overflow; all seven component toggles, 2025 cutoff, reserve overlay, no-reserve, funding mode and return/DD mode verified.

## IMBA current model and original account disclosure (2026-11-27)

- Restored **IMBA R2B regression** daily equity histories from the latest IMBA Bot research run (2024-01-01 to 2026-10-30). These are **separate 1,000-EUR-start portfolio simulations** (10x R2B trades, annual regression fit only on previous years, 0.06% fee per side, KuCoin Funding and margin/liquidation harness). This is **not** the original 7's historical IMBA TP/SL constituent, which remains a separate checkbox.
- Huber_bin: 15,129.23 EUR on the site cutoff 2026-10-30, 15,286.66 EUR on the full research cutoff 2026-11-04. WLS_bin: 13,711.72 EUR on site cutoff (13,817.54 EUR on full cutoff); Ridge_bin and OLS_bin similarly available. Full replay exactly reconciles to the source's published harness ranking `durch_rang_regelB.csv` to cents. Historical sample results, NOT out-of-sample or live.
- Footer account group **“Original 7 + Protected Cash Reserve”** is now collapsed by default. Tapping expands the detailed EUR account/cash/no-reserve comparisons **and adds both Original7 owned account and its matching protected cash to the chart**, preserving all other selected bots/assets. Tapping again folds and disables only that pair. It never rewrites the chosen reserve percentage or the selected comparison bots. Cash stays green.
- Only **one main/featured model** is white at a time. With original7/cash group opened, Original7 is white; otherwise the user-selected main model (IMBA Huber by default) is white. XYZ3 is permanently lavender unless explicitly chosen as the focused model; other models keep distinct hues. Black/dark background, same shared EUR SYMLOG scale for all wealth and protected cash lines.
- **Literatur / Papier C** is 80% IMBA Ziel/Stop TP/SL challenger plus 20% US-morning volatility-adjusted short (`bots/literatur/papier_c.py`), not an independent single literature-paper signal. Its 2024/2025 reported outcomes look strong, but independently audited 2026 suffered -98.72% maximum drawdown and a refill; the historical Original7 constituent comparison ends 2025, now visibly labelled with that cutoff and risk warning.
- Relevant source: `quant-main/quant_experiments/imba_regression_2026-11-27/durch_rank.py`, ranking `durch_rang_regelB.csv`, and `quant_experiments/strategie_turnier_2026-11-11/bots/literatur/BERICHT_LITERATUR.md`. Repro builders and source-verified daily curves: `quant-main/research/overnight_orb_indices_20261123/regression_overlay_20261126/causal_3axis_20261127/{export_current_imba_20261127.py,build_latest_imba_20261127.py,build_original7_fold_20261127.py,imba_current_20261127/imba_regression_equity.json}`. No live trading changes.
