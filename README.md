# Area Fire Analysis v1.4 - Regional Dynamic Adaptation
## 地域動的対応火災分析システム v1.4

**🌍 Multi-Regional Fire Detection & Analysis Pipeline**  
**International Response System for Forest Fire Monitoring**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![CUDA](https://img.shields.io/badge/CUDA-Supported-green.svg)](https://nvidia.com/cuda)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 🚀 Project Overview - プロジェクト概要

This system represents a major evolution from single-region fire analysis to **dynamic multi-regional adaptation**. Originally designed for Asia-Pacific, v1.4 introduces comprehensive regional expansion capabilities with proven performance across different continental fire patterns.

### ✨ Key Achievements
- **🌎 Regional Expansion**: Successfully adapted from Asia-Pacific to South America
- **📈 Performance Scaling**: 154% increase in fire detection capacity (106K+ detections)
- **🔬 Quality Enhancement**: 0.698 clustering quality score with 0% noise ratio
- **⚡ Speed Optimization**: 82.9s processing time for 15K samples
- **🛠️ Dynamic Architecture**: Configurable regional parameters for global deployment

---

## 🎯 Featured Regions - 対応地域

### ✅ South America (Implemented)
- **Target Country**: Chile (with regional coverage)
- **Coverage**: -82°W to -35°W, -56°S to 15°N
- **Performance**: 106,775 fire detections → 15,000 processed
- **Quality Score**: 0.698/1.0
- **Cluster Count**: 12 optimal clusters
- **Processing Time**: 82.90 seconds

### 🔄 Europe (In Development)
- **Target Country**: Italy (planned)
- **Coverage**: Mediterranean and Alpine regions
- **Expected Performance**: Similar to South America scale

---

## 🏗️ Architecture Features - アーキテクチャ特徴

### 1. Dynamic Regional Configuration
```json
{
  "region": "south_america",
  "nasa_firms": {
    "area_params": {
      "south": -56.0, "north": 15.0,
      "west": -82.0, "east": -35.0
    }
  },
  "report": {
    "region_name": "South America",
    "focus_country": "Chile"
  }
}
```

### 2. Adaptive Clustering Intelligence
- **Large Dataset**: FAISS k-means (3000+ samples)
- **Small Dataset**: HDBSCAN (< 3000 samples)
- **Quality Metrics**: Multi-criteria evaluation
- **GPU Acceleration**: CUDA-optimized processing

### 3. Comprehensive Analysis Pipeline
1. **Data Collection**: NASA FIRMS satellite API
2. **Quality Filtering**: Confidence-based selection
3. **Text Embedding**: sentence-transformers/all-MiniLM-L6-v2
4. **Adaptive Clustering**: Dynamic algorithm selection
5. **Feature Analysis**: Geographic, temporal, intensity patterns
6. **Visualization**: t-SNE plots, distribution analysis
7. **Report Generation**: Automated comprehensive reports

---

## 📊 Proven Performance Metrics

| Region | Fire Detections | Processing Time | Quality Score | Clusters | Success Rate |
|--------|----------------|-----------------|---------------|----------|--------------|
| **South America** | 106,775 → 15,000 | 82.90s | 0.698 | 12 | 100% |
| Asia-Pacific | 42,120 → 15,000 | ~85s | ~0.65 | 10 | 100% |
| **Improvement** | **+154%** | **+3% faster** | **+7%** | **+20%** | **Stable** |

---

## 🚀 Quick Start Guide

### Prerequisites
```bash
# Python 3.8+ with virtual environment
python -m venv .venv
.venv\Scripts\Activate.ps1  # Windows
# source .venv/bin/activate  # Linux/Mac

# Install dependencies
pip install -r requirements.txt
```

### Basic Execution
```bash
# South America Analysis
python south_america_firms_pipeline.py

# Expected Output: 13 files including comprehensive report
# Processing Time: ~83 seconds
# Quality Score: 0.698+
```

### Configuration
Edit `config_south_america_firms.json` for customization:
- **Geographic bounds**: Adjust lat/lon ranges
- **Sample limits**: Modify max_samples for performance
- **Clustering**: Tune cluster count and quality thresholds

---

## 📁 Repository Structure

```
area-fire-analysis-v1-4/
├── 🔧 Core Pipeline
│   ├── south_america_firms_pipeline.py    # Main South America pipeline
│   ├── fire_analysis_report_generator.py  # Dynamic report generation
│   ├── cluster_feature_analyzer.py        # Regional feature analysis
│   └── adaptive_clustering_selector.py    # Intelligent clustering
│
├── ⚙️ Configuration
│   └── config_south_america_firms.json    # South America settings
│
├── 📝 Documentation
│   ├── README.md                          # Main project documentation
│   ├── README_v1-4_area.md               # Architecture design document
│   └── Quick_Guide_southamerica.md       # South America practical guide
│
├── 🛠️ Utilities
│   └── scripts/
│       ├── data_collector.py              # NASA FIRMS API interface
│       ├── embedding_generator.py         # Text embedding creation
│       ├── model_loader.py               # ML model management
│       ├── visualization.py              # Plot generation
│       └── clustering.py                 # Clustering algorithms
│
└── 📋 Setup
    └── requirements.txt                   # Python dependencies
```

---

## 🔬 Technical Innovations

### 1. Regional Adaptation Pattern
- **Geographic Intelligence**: Dynamic coordinate system handling
- **Cultural Localization**: Region-specific report generation
- **Performance Scaling**: Adaptive processing based on data volume

### 2. Quality Assurance System
```python
quality_metrics = {
    "silhouette": 0.3,      # Cluster separation
    "calinski_harabasz": 0.2, # Cluster density
    "davies_bouldin": 0.2,   # Cluster compactness
    "noise_penalty": 0.2,    # Outlier handling
    "cluster_balance": 0.1   # Size distribution
}
```

### 3. Multi-Scale Processing
- **Embedding**: 384-dimensional semantic vectors
- **Clustering**: Up to 100K+ sample capacity
- **Visualization**: High-resolution geographic plots
- **Reporting**: Multi-language comprehensive analysis

---

## 📈 Use Cases & Applications

### 1. Emergency Response
- **Real-time Monitoring**: 10-day rolling analysis
- **Risk Assessment**: High-confidence fire detection (50%+)
- **Geographic Targeting**: Country-specific focus areas

### 2. Research & Analysis
- **Pattern Discovery**: Temporal and spatial fire behaviors
- **Regional Comparison**: Cross-continental fire analysis
- **Climate Studies**: Long-term fire trend analysis

### 3. Policy & Planning
- **Resource Allocation**: Data-driven firefighting deployment
- **Prevention Strategy**: High-risk area identification
- **International Cooperation**: Standardized regional reporting

---

## 🌟 Success Stories

### South America Deployment
> **"Successfully processed 106,775 South American fire detections with 0.698 quality score, identifying 12 distinct fire patterns across Brazil, Chile, Argentina, and Peru. Processing time: 82.90 seconds."**

### Key Discoveries
- **Brazil Central**: Highest fire density (3,449 detections)
- **Chile Andes**: High-intensity fires (347K brightness)
- **Argentina Pampas**: Medium-intensity patterns
- **Peru Amazon**: Scattered fire activity

---

## 🛠️ Development Roadmap

### ✅ Completed (v1.4)
- [x] South America regional adaptation
- [x] Dynamic configuration system
- [x] Comprehensive documentation
- [x] Performance optimization
- [x] Quality assurance framework

### 🔄 In Progress
- [ ] Europe configuration (Italy focus)
- [ ] Automated testing framework
- [ ] API endpoint development

### 🎯 Future Versions (v1.5+)
- [ ] North America expansion
- [ ] Real-time streaming analysis
- [ ] Mobile application interface
- [ ] Machine learning predictions
- [ ] Multi-language UI support

---

## 📞 Support & Contribution

### Documentation
- **Technical Design**: `README_v1-4_area.md`
- **Quick Start**: `Quick_Guide_southamerica.md`
- **API Reference**: Coming in v1.5

### Contributing
1. Fork the repository
2. Create feature branch (`git checkout -b feature/new-region`)
3. Follow regional adaptation patterns
4. Submit pull request with performance metrics

### Issues & Questions
- **GitHub Issues**: Technical problems and feature requests
- **Performance**: Optimization and scaling questions
- **Regional Expansion**: New area implementation guidance

---

## 📜 License & Acknowledgments

### License
MIT License - See LICENSE file for details

### Acknowledgments
- **NASA FIRMS**: Fire Information for Resource Management System
- **Sentence Transformers**: Hugging Face embedding models
- **FAISS**: Facebook AI Similarity Search
- **scikit-learn**: Machine learning algorithms

### Citation
```
Area Fire Analysis v1.4 - Regional Dynamic Adaptation
GitHub: https://github.com/tk-yasuno/area-fire-analysis-v1-4
Year: 2025
```

---

## 🎉 Get Started Today!

```bash
git clone https://github.com/tk-yasuno/area-fire-analysis-v1-4.git
cd area-fire-analysis-v1-4
pip install -r requirements.txt
python south_america_firms_pipeline.py
```

**Experience the power of regional fire analysis in under 2 minutes!**

---

*Built with ❤️ for global forest fire monitoring and emergency response*  
*v1.4 Regional Dynamic Adaptation - Proven performance across continents*