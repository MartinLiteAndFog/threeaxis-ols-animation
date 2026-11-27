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
