# 予測保守 (Predictive Maintenance) プロジェクト
## Machine Failure Classification & Model Interpretation with SHAP

このプロジェクトは、AI4I-PMDI 2024データセットを使用して製造現場における機械故障予測と説明可能なAI技術を実装したものです。
This project demonstrates machine failure prediction and explainable AI techniques for manufacturing environments using the AI4I-PMDI 2024 dataset.

---

## 1. プロジェクト概要 / Project Overview
AI4I-Predictive Maintenance Datasetを使用して、機械の稼働センサーデータ（温度、回転数、トルクなど）から故障の種類を分類します。
The project uses the AI4I-Predictive Maintenance Dataset to classify machine failures and their types based on operational sensor data (temperature, RPM, torque, etc.).

- **課題 (Problem)**: 予期せぬ設備停止による経済的損失の防止。
- **解決策 (Solution)**: LightGBMによる高精度予測とSHAPによるモデル解釈性の確保。

---

## 2. 技術スタック / Technical Stack
- **言語 (Language)**: Python 3.14+
- **主要ライブラリ (Core Libraries)**:
  - `LightGBM`: 高速な勾配ブースティングによるマルチクラス分類
  - `Scikit-learn`: データ前処理とモデル評価
  - `SHAP (Explainable AI)`: モデル予測と特徴量寄与の解釈
  - `Imbalanced-learn (SMOTE)`: 不均衡クラスの処理
  - `Pandas & NumPy`: データ操作と数値計算

---

## 3. プロジェクトパイプライン / Project Pipeline

### Phase 1: データ前処理と特徴量エンジニアリング / Data Preprocessing & Feature Engineering
- データセットの読み込みと検証（形状、欠損値、データ型）
- 中央値補完による欠損値処理
- ドメイン固有の特徴量作成：
  - 温度差（熱ストレス）
  - 動力指標（トルク × 回転速度）
- 非予測的管理列の削除
- 訓練・テスト分割時のクラス分布維持

### Phase 2: 不均衡データ処理とモデル訓練 / Imbalanced Data Handling & Model Training
- SMOTE（合成少数オーバーサンプリング）によるクラス不均衡の解決
- 1000回のブースティング反復によるLightGBM分類器の訓練
- 分類メトリクスを使用したモデル性能評価

### Phase 3: 説明可能なAI (SHAP分析) / Explainable AI (SHAP Analysis)
- グローバル解釈：故障予測を駆動する主要特徴量の特定
- ローカル解釈：特定の故障事例のフォースプロット分析
- 動的故障クラス検出（少数クラス）

---

## 4. 可視化結果 / Visualization Results

### グローバル特徴量重要度 / Global Feature Importance
全テスト事例におけるモデル予測に対するセンサー値の影響度を示します。
Shows which sensor values most strongly influence the model's equipment failure predictions across all test cases.
![Impact of Key Variables on Equipment Failure Risk](Impact%20of%20Key%20Variables%20on%20Equipment%20Failure%20Risk.png)

### 事例別故障分析 / Case-Specific Failure Analysis
特定の故障イベントの根本原因を詳細な特徴量寄与分解で示します。
Demonstrates root causes for a specific failure event with detailed feature contribution breakdown.
![Root Cause Diagnostics for a Specific Failure Event](Root%20Cause%20Diagnostics%20for%20a%20Specific%20Failure%20Event.png)

---

## 5. セットアップ / Setup
```bash
pip install -r requirements.txt
