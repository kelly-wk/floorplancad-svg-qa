# FloorPlanCAD：SVG形状の品質監査 / FloorPlanCAD: SVG Geometry Quality Audit

[紹介ページを開く / Open the presentation page](https://kelly-wk.github.io/floorplancad-svg-qa/)

> **QAプロトタイプ検証済み・MLゲート未通過 / Validated QA prototype / ML gate blocked**  
> 公開ケーススタディ / Public case study

## 概要 / Overview

SVG図面を機械学習用ラベルへ変換する前に、単位・変換・形状整合性を監査する品質ゲート。

A quality gate that audits units, transforms, and geometry before SVG floor plans become machine-learning labels.

## 主なポイント / Highlights

1. **未対応のSVG構文を黙って近似せず、境界付きパーサーが明示的に記録。**  
   The bounded parser logs unsupported SVG constructs instead of silently approximating them.
2. **mm単位を宣言した合成ゴールデンフィクスチャで二重境界形状を検証。**  
   A synthetic declared-millimeter golden fixture checks double-boundary geometry.
3. **物理スケール、利用権、ゴールデンセットが揃わない限りラベル生成を停止するMLゲートを定義。**  
   Defined an ML gate that blocks label generation until physical scale, usage rights, and a golden set are available.

## 研究の流れ / Research Flow

| 段階 / Stage | 内容 / Evidence |
|---|---|
| **課題 / Problem** | 多様なSVG図面を無検証で学習ラベルへ変換すると、単位や座標変換の誤りが教師データへ混入する。<br>Converting heterogeneous SVG plans directly into labels can inject unit and transform errors into training data. |
| **方法 / Method** | XML構造、座標変換、単位、閉曲線、未対応要素を段階的に監査する。<br>Audit XML structure, coordinate transforms, units, closed geometry, and unsupported elements in stages. |
| **検証 / Validation** | 既知寸法を持つ合成ゴールデンケースで形状計算と拒否条件を確認する。<br>Check geometry calculations and rejection conditions against synthetic golden cases with known dimensions. |
| **成果 / Outcome** | データ品質を可視化するプロトタイプは成立したが、実図面によるML検証はゲート未通過。<br>The data-quality prototype is validated, while real-plan ML validation remains blocked by the release gate. |

## 使用手法 / Methods

Python, SVG and XML parsing, Affine transforms, Unit conversion, Geometry QA, Group-aware splitting

## 限界と適用範囲 / Limitations & Scope

- 実図面の壁意味論、U-Net学習、外部図面での性能は未検証。  
  Wall semantics on real plans, U-Net training, and performance on external drawings remain unvalidated.

## 公開範囲 / Publication Boundary

合成フィクスチャに基づくQA設計は紹介できるが、実図面と派生結果は公開対象外。

The synthetic-fixture QA design can be described, but real drawings and derived results are excluded from publication.

---

この文書は公開可能な範囲だけで構成されています。  
This document contains only material cleared for public presentation.
