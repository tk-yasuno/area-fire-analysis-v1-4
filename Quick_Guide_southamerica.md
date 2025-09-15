# Quick Guide: South America Fire Detection Analysis
## 南米地域火災検知分析クイックガイド

**Version**: v1.4 Regional Dynamic Adaptation  
**Date**: 2025年9月15日  
**Target Region**: South America (Chile focus)  
**Pipeline**: south_america_firms_pipeline.py

---

## 🚀 Quick Start - クイックスタート

### 基本実行コマンド
```bash
# 仮想環境アクティベート
.venv\Scripts\Activate.ps1

# 南米版パイプライン実行
python south_america_firms_pipeline.py
```

**実行時間**: 約82.90秒（15,000サンプル処理）  
**必要メモリ**: 約16GB GPU メモリ推奨

---

## 📊 Performance Overview - パフォーマンス概要

### ✅ 実証済み性能指標

| 指標 | 値 | 備考 |
|------|-----|------|
| **処理速度** | 82.90秒 | 15,000サンプル |
| **品質スコア** | 0.698/1.0 | 高品質クラスタリング |
| **検出効率** | 181 件/秒 | (15,000÷82.90) |
| **データ効率** | 96,059→15,000 | 84%削減で安定性確保 |
| **クラスター数** | 12個 | 最適分離達成 |
| **ノイズ率** | 0.0% | 完全クラスタリング |

### 🌍 地域カバレッジ実績

```
対象範囲: 南米全域
- 経度: -82.0°W から -35.0°W (47度幅)
- 緯度: -56.0°S から 15.0°N (71度幅)

実際データ収集:
- 総検知数: 106,775件 (10日間)
- 高信頼度: 96,059件 (≥50%信頼度)
- 処理対象: 15,000件 (システム安定性考慮)
```

---

## 🎯 Key Features - 主要機能

### 1. 高度データ収集
- **NASA FIRMS API**: リアルタイム衛星データ
- **VIIRS_SNPP_NRT**: 次世代極軌道衛星
- **信頼度フィルタ**: 50%以上のみ処理
- **地域特化**: チリ中心の南米最適化

### 2. 機械学習最適化
- **適応的アルゴリズム**: 大規模データ用FAISS k-means
- **品質保証**: 複合品質評価指標
- **GPU加速**: CUDA対応（AVX2フォールバック）
- **スケーラブル**: 10万件超データ対応

### 3. 包括的分析
- **地理的分析**: 4大火災地域特定（ブラジル、チリ、アルゼンチン、ペルー）
- **時間パターン**: 日中・夜間活動サイクル分析
- **強度分析**: 高・中・低強度火災群分離
- **統計分析**: 平均信頼度61.3%、明度334.5K

---

## 📁 Output Structure - 出力ファイル構造

### 生成ファイル一覧（13ファイル）

```
data_firms_south_america_202509151034/
├── 📊 データファイル
│   ├── nasa_firms_data.csv                 # 元データ（15,000件）
│   ├── south_america_fires_clustered.csv   # クラスタリング結果
│   ├── final_south_america_results.json    # 最終結果サマリー
│   └── embeddings.npy                      # 機械学習特徴ベクトル
│
├── 🖼️ 可視化ファイル
│   ├── tsne_plot.png                       # t-SNE次元削減プロット
│   ├── score_distribution.png              # スコア分布図
│   ├── cluster_geographic_distribution.png  # 地理的分布分析
│   ├── cluster_intensity_analysis.png      # 強度分析図
│   ├── cluster_regional_analysis.png       # 地域特性分析
│   └── cluster_temporal_patterns.png       # 時間パターン分析
│
├── 📝 レポート
│   └── comprehensive_fire_analysis_report.md # 包括的分析レポート
│
└── 📁 データ処理フォルダ
    ├── raw/                                # 生データ
    └── cleaned/                            # 前処理済みデータ
```

---

## 🔧 Configuration - 設定詳細

### 設定ファイル: `config_south_america_firms.json`

#### 重要パラメータ
```json
{
  "nasa_firms": {
    "area_params": {
      "south": -56.0,    // パタゴニア南端
      "north": 15.0,     // カリブ海・ベネズエラ
      "west": -82.0,     // ペルー西海岸
      "east": -35.0      // ブラジル東海岸
    },
    "confidence_threshold": 50,  // 信頼度50%以上
    "days_back": 10             // 過去10日間
  },
  "clustering": {
    "adaptive_threshold": 3000,  // 3000件超でFAISS k-means
    "kmeans_n_clusters": 12     // 最適クラスター数
  },
  "processing": {
    "max_samples": 15000        // 処理上限（安定性確保）
  }
}
```

---

## 🌟 Results Highlights - 分析結果ハイライト

### 主要発見事項

#### 🔥 火災分布パターン
1. **最大クラスター**: 3,449件（ブラジル中央部）
2. **高強度火災**: 平均明度347-350K（チリ・アルゼンチン）
3. **地域特性**: 4つの明確な火災地域
4. **時間パターン**: 明確な日中・夜間サイクル

#### 📈 クラスター品質分析
- **CLUSTER_4**: 3,449件（最大規模・ブラジル）
- **CLUSTER_0**: 1,545件（高強度・ブラジル）
- **CLUSTER_10**: 1,522件（高強度・南米）
- **CLUSTER_5**: 1,477件（低強度・南米）

### 地理的インサイト
```
🌎 主要火災地域:
- ブラジル中央部: 最高密度火災活動
- チリ中央部: 高強度火災パターン
- アルゼンチン北部: 中程度活動
- ペルー東部: 散発的火災活動
```

---

## ⚡ Performance Tips - パフォーマンス最適化

### 1. システム要件
- **GPU**: CUDA対応（推奨）16GB以上
- **CPU**: AVX2サポート
- **RAM**: 8GB以上
- **ストレージ**: 2GB空き容量

### 2. 実行最適化
```bash
# GPU確認
nvidia-smi

# メモリ使用量監視
python -c "import torch; print(f'GPU Memory: {torch.cuda.get_device_properties(0).total_memory/1024**3:.1f}GB')"

# バッチサイズ調整（config内）
"batch_size": 64  # GPU性能に応じて調整
```

### 3. トラブルシューティング
| 問題 | 解決策 |
|------|--------|
| GPU不足 | `"device": "cpu"`に変更 |
| メモリエラー | `max_samples`を10000に削減 |
| 品質低下 | `confidence_threshold`を60に上昇 |
| 処理遅延 | `batch_size`を32に削減 |

---

## 🔄 Workflow Integration - ワークフロー統合

### 標準的な実行フロー

```bash
# 1. 環境準備
.venv\Scripts\Activate.ps1

# 2. 設定確認
python -c "import json; print(json.load(open('config_south_america_firms.json'))['region'])"

# 3. パイプライン実行
python south_america_firms_pipeline.py

# 4. 結果確認
dir data_firms_south_america_* /od
```

### 継続的分析のための自動化
```powershell
# スケジュール実行用バッチファイル
@echo off
cd /d "C:\Users\yasun\DisasterSentiment"
call .venv\Scripts\Activate.ps1
python south_america_firms_pipeline.py
echo "South America Analysis completed at %date% %time%" >> analysis_log.txt
```

---

## 📊 Comparison with Asia-Pacific - アジア太平洋版との比較

| 指標 | 南米版 | アジア太平洋版 | 改善度 |
|------|--------|----------------|--------|
| **火災検知数** | 106,775件 | 42,120件 | +154% |
| **処理時間** | 82.90秒 | ~85秒 | 同等 |
| **品質スコア** | 0.698 | ~0.65 | +7% |
| **クラスター数** | 12個 | 10個 | +20% |
| **地域カバー** | 南米全域 | アジア太平洋 | 2.5倍の火災活動 |

### 技術的優位性
- **地域適応**: 南米固有の地理特性に最適化
- **スケーラビリティ**: より大規模なデータ処理能力
- **品質向上**: 改良されたクラスタリングアルゴリズム
- **レポート**: 動的地域対応の包括的レポート生成

---

## 🚀 Next Steps - 次のステップ

### 1. 即座に実行可能
```bash
# 異なる期間での分析
# config内 "days_back": 30 に変更して月次分析

# より詳細な地域分析
# 特定国のみの座標範囲に調整
```

### 2. 拡張可能性
- **ヨーロッパ版**: 同様の手法でイタリア中心の分析
- **北米版**: カナダ・アメリカの森林火災分析
- **リアルタイム**: 1日間隔での継続監視

### 3. 高度な分析
- **季節分析**: 月別・四半期別の火災パターン
- **気候相関**: 気温・湿度との関係分析
- **予測モデル**: 機械学習による火災予測

---

## 📞 Support & Documentation - サポート・ドキュメント

### 関連ドキュメント
- `README_v1-4_area.md`: 地域動的対応アーキテクチャ設計
- `config_south_america_firms.json`: 南米特化設定
- `comprehensive_fire_analysis_report.md`: 詳細分析レポート

### 技術サポート
- **GitHub Repository**: asia-pacific-fire-analysis
- **Issues**: GitHub Issues で技術的質問
- **Performance**: パフォーマンス最適化相談

---

## ✅ Checklist - 実行チェックリスト

### 事前準備
- [ ] Python仮想環境アクティベート
- [ ] GPU/CUDA動作確認
- [ ] 設定ファイル確認
- [ ] 十分なディスク容量（2GB以上）

### 実行確認
- [ ] パイプライン正常終了
- [ ] 13ファイル生成確認
- [ ] 品質スコア0.6以上
- [ ] レポートファイル確認

### 結果活用
- [ ] 可視化ファイル確認
- [ ] レポート内容理解
- [ ] 結果データ保存
- [ ] 必要に応じて他地域展開

---

**🎉 南米地域火災検知分析システム v1.4 - 実証済み高性能地域適応パイプライン**

*Last Updated: 2025年9月15日 - Performance validated with 106,775 real fire detections*