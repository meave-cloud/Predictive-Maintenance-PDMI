# 予測保守 (Predictive Maintenance) プロジェクト
## Machine Failure Classification & Model Interpretation with SHAP

このプロジェクトは、製造現場における機械の故障予測と、その要因を AI で可視化する手法をまとめたポートフォリオです。
This project demonstrates machine failure prediction and factor visualization using AI for manufacturing environments.

---

## 1. プロジェクト概要 / Project Overview
AI4I-Predictive Maintenance Dataset を使用し、機械の稼働データ（温度、回転数、トルクなど）から故障の有無とその種類を分類します。
Using the AI4I-Predictive Maintenance Dataset, this project classifies machine failures based on operational data (temperature, RPM, torque, etc.).

- **課題 (Problem)**: 予期せぬ設備停止による経済的損失の抑制。
- **解決策 (Solution)**: LightGBM による高精度な予測と、SHAP による予測根拠の可視化。

---

## 2. 技術スタック / Technical Stack
- **Language**: Python 3.14
- **Libraries**: 
  - `LightGBM`: 勾配ブースティングを用いた高速・高精度な分類。
  - `Scikit-learn`: データ前処理および評価。
  - `SHAP (Explainable AI)`: ブラックボックス化したモデルの予測要因を可視化。
  - `Imbalanced-learn`: 不均衡データ（故障データ）への対応。

---

## 3. 分析フロー / Workflow
1. **EDA & Preprocessing**: センサーデータの相関分析とクリーニング。
2. **Handling Imbalanced Data**: 故障データが少ないため、重み付け調整等を実施。
3. **Modeling**: LightGBM を用いたマルチクラス分類。
4. **Interpretation (XAI)**: SHAP を使用し、個別の故障予測に対する寄与度を分析。

---

## 4. 可視化結果 / Visualization
リポジトリ内の `shap_waterfall_normal_case.png` は、特定のデータポイントにおいて、どのセンサー値が故障予測に最も影響を与えたかを示しています。
The `shap_waterfall_normal_case.png` file demonstrates which sensor values most influenced the failure prediction for a specific data point.
![SHAP Analysis Result](shap_waterfall_normal_case.png)


---

## 5. セットアップ / Setup
```bash
pip install -r requirements.txt
