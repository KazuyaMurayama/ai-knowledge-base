---
title: "3倍レバレッジNASDAQ投資戦略：バックテスト最終結果"
date: 2026-02-06
source: claude
tags: [investment, backtest, nasdaq, leverage, data-analysis, python]
use_case: advice
perspective: research
topic_area: data-science
---

## 要点

47年間（1974-2021）のNASDAQ Composite Indexデータで255+戦略をバックテスト。推奨戦略Ens2(Asym+Slope)はSharpe 1.031、MaxDD -48.17%、最悪5年間CAGRでもプラス圏（+1.41%）を達成。4層構造（DD制御+非対称EWMA+VTレバレッジ+Slope乗数）で、年間取引わずか30回。

## 詳細

### 推奨戦略: Ens2(Asym+Slope)

| 指標 | 値 | ベースライン(BH 3x) |
|---|---|---|
| CAGR | 28.58% | 19.94% |
| Sharpe | 1.031 | 0.607 |
| MaxDD | -48.17% | -99.89% |
| Worst5Y | +1.41% | -60.07% |
| 取引回数 | 30回/47年 | 0 |

### 4層シグナルの仕組み

```
Layer 1: DD制御 → 200日高値から-18%で退避、92%回復で復帰
Layer 2: AsymEWMA → 下落時Span=5(高速反応)、上昇時Span=20(低速反応)
Layer 3: VTレバレッジ → leverage = min(0.25 / AsymVol, 1.0)
Layer 4: SlopeMult → MA200傾きのZ-score化 → 乗数clip(0.7+0.3×z, 0.3, 1.5)
```

### 研究の進化（R1→R3）

- **R1(32戦略)**: ボラティリティ管理がSharpeを+30%改善する発見
- **R2(75戦略)**: EWMA Span=10がSimple Volを大幅に上回る（Sharpe +28.6%）
- **R3(148戦略)**: DD最適化+アンサンブルで低回転率を維持しつつ性能向上

### 危機年パフォーマンス

- **ドットコムバブル(2000-2002)**: 完全回避（0%損失）。BH 3xは-89.6%
- **金融危機(2008)**: -5.1%〜-9.8%。DDベースラインは-28.2%

**出典リポジトリ**: NASDAQ_backtest

## 活用シーン

- レバレッジ投資戦略のリスク管理手法の参考
- ボラティリティターゲティングの実装パターン
- バックテスト研究の方法論（段階的ラウンド検証）の参考
