# 🌲 Tree Cutting Priority Analysis - Fire Creek

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![GeoPandas](https://img.shields.io/badge/GeoPandas-1.0+-green.svg)](https://geopandas.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **Spatial Data Analysis - Homework 2**  
> Multi-criteria decision analysis (MCDA) for wildfire risk mitigation through strategic tree cutting prioritization.

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Usage](#-usage)
- [Methodology](#-methodology)
- [Results](#-results)
- [Output Files](#-output-files)
- [Visualization](#-visualization)
- [Authors](#-authors)

---

## 🎯 Overview

This project identifies and prioritizes tree cutting zones for wildfire risk mitigation in the **Fire Creek** area using Python-based spatial analysis. The analysis evaluates **80 grid zones** across **5 weighted criteria** to produce normalized priority scores (0-100) classified into actionable priority classes.

### Key Objectives

1. Calculate tree cutting priority for each zone in the cutting grid
2. Apply multi-criteria decision analysis (MCDA) with weighted factors
3. Normalize all scores to a 0-100 scale for consistent comparison
4. Classify zones into priority classes: **Low**, **Medium**, **High**, **Critical**
5. Generate visualization charts for decision-making support

---

## ✨ Features

- **Multi-Factor Analysis**: Evaluates 5 different risk factors
- **Weighted Scoring**: Customizable weights for each factor
- **Normalized Scores**: All factors scaled to 0-100 for fair comparison
- **Priority Classification**: Automatic classification into 4 priority levels
- **Multiple Output Formats**: Shapefile, GeoPackage, and CSV
- **Professional Visualization**: 3 comprehensive charts (Bar, Pie, and Top 10 zones)
- **QGIS Compatible**: Direct integration with QGIS for mapping

---

## 📁 Project Structure

```
tree-cutting-priority/
├── tree_data/                      # Input shapefiles
│   ├── CuttingGrids.shp           # Main analysis grid (80 zones)
│   ├── SBNFMortalityt.shp         # Tree mortality data
│   ├── Communityfeatures.shp      # Community infrastructure
│   ├── EgressRoutes.shp           # Evacuation routes
│   ├── PopulatedAreast.shp        # Populated areas
│   ├── Transmission.shp           # High-voltage lines
│   ├── SubTransmission.shp        # Sub-transmission lines
│   ├── DistCircuits.shp           # Distribution circuits
│   ├── Substations.shp            # Power substations
│   ├── PoleTopSubs.shp            # Pole-top substations
│   └── TownBoundary.shp           # Town boundary reference
│
├── output/                         # Generated outputs
│   ├── TreeCuttingPriority_*.shp  # Priority shapefile (timestamped)
│   ├── TreeCuttingPriority_*.gpkg # GeoPackage output (timestamped)
│   ├── TreeCuttingPriority_v2.shp # Latest version shapefile
│   ├── TreeCuttingPriority_v2.gpkg# Latest version GeoPackage
│   └── TreeCuttingPriority_Charts.png  # Visualization charts
│
├── visual-outputs/                 # Additional visualizations
│   ├── layers-names.png           # Layer name reference
│   └── layers-visual.png          # Visual layer overview
│
├── report/                         # Analysis reports (future use)
│
├── tree_cutting_priority.py       # Main analysis script
└── README.md                       # This file
```

---

## 🛠 Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager

### Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/tree-cutting-priority.git
cd tree-cutting-priority
```

### Step 2: Create Virtual Environment (Recommended)

```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# Linux/Mac
source .venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install geopandas pandas numpy matplotlib
```

### Required Packages

| Package | Version | Purpose |
|---------|---------|---------|
| geopandas | ≥0.11.0 | Spatial data manipulation and GIS operations |
| pandas | ≥1.3.0 | Data processing and analysis |
| numpy | ≥1.21.0 | Numerical calculations and array operations |
| matplotlib | ≥3.5.0 | Chart visualization and plotting |

### Important Notes

- Ensure your data paths in [tree_cutting_priority.py](tree_cutting_priority.py) are correctly set:
  ```python
  DATA_DIR = Path(r"C:/Users/baram/Desktop/Raster/data")
  OUTPUT_DIR = Path(r"C:/Users/baram/Desktop/Raster/output")
  ```
- Update these paths to match your local directory structure

---

## 🚀 Usage

### Running the Analysis

```bash
python tree_cutting_priority.py
```

### Expected Console Output

```
============================================================
Tree Cutting Priority Analysis - Fire Creek
============================================================

[STEP 1] Loading shapefiles...
  - CuttingGrids: 80 zones loaded
  - SBNFMortalityt (Tree Mortality): X features loaded
  - Communityfeatures: X features loaded
  - EgressRoutes: X features loaded
  - PopulatedAreast: X features loaded
  - Transmission: X features loaded
  - SubTransmission: X features loaded
  - DistCircuits: X features loaded
  - Substations: X features loaded
  - PoleTopSubs: X features loaded
  - TownBoundary: X features loaded

[STEP 2] Checking and aligning coordinate reference systems...
  Target CRS: EPSG:26711
  All layers reprojected to target CRS

[STEP 3] Initializing priority calculation...

[STEP 4] Calculating Tree Mortality Score...
  Mortality scores calculated (max raw: X.XX)

[STEP 5] Calculating Community Features Score...
  Community scores calculated (max raw: X.XX)

[STEP 6] Calculating Egress Routes Score...
  Egress scores calculated (max raw: X.XX)

[STEP 7] Calculating Populated Areas Score...
  Populated area scores calculated (max raw: X.XX)

[STEP 8] Calculating Electric Utilities Score...
  Utility scores calculated (max raw: X.XX)

[STEP 9] Calculating Overall Tree Cutting Priority...
  Weights applied:
    - Tree Mortality: 30%
    - Community Features: 15%
    - Egress Routes: 20%
    - Populated Areas: 20%
    - Electric Utilities: 15%

[STEP 10] Saving results...
  Output CRS: EPSG:26711
  Geometry type: ['Polygon']
  Total features: 80
  Shapefile saved: output/TreeCuttingPriority_YYYYMMDD_HHMMSS.shp
  GeoPackage saved: output/TreeCuttingPriority_YYYYMMDD_HHMMSS.gpkg
  CSV saved: output/TreeCuttingPriority.csv

============================================================
TREE CUTTING PRIORITY ANALYSIS - SUMMARY
============================================================

[Priority Distribution and Statistics]

[STEP 12] Generating visualization charts...
  Charts saved: output/TreeCuttingPriority_Charts.png

============================================================
Analysis Complete!
============================================================
```

---

## 📊 Methodology

### Analysis Workflow

```
CuttingGrids (80 Zones)
        ↓
① Load & Align CRS → EPSG:26711
        ↓
② Calculate Factor Scores → 5 factors
        ↓
③ Normalize Scores → 0-100 scale
        ↓
④ Apply Weighted MCDA → Priority Score
        ↓
⑤ Classify Priority → Low/Medium/High/Critical
        ↓
⑥ Generate Charts → Visualization
```

### Factor Weights

| Factor | Weight | Description |
|--------|:------:|-------------|
| **Tree Mortality** | 30% | Dead/dying trees indicating fire fuel load |
| **Egress Routes** | 20% | Emergency evacuation route protection |
| **Populated Areas** | 20% | Residential zone life safety |
| **Community Features** | 15% | Critical infrastructure protection |
| **Electric Utilities** | 15% | Power infrastructure protection |

### Priority Classification

| Class | Score Range | Action Required |
|-------|:-----------:|-----------------|
| 🔴 **Critical** | 75 - 100 | Immediate action required |
| 🟠 **High** | 50 - 74 | Near-term action needed |
| 🟡 **Medium** | 25 - 49 | Scheduled maintenance |
| 🟢 **Low** | 0 - 24 | Routine monitoring |

### Normalization Formula

```python
Normalized_Score = (Raw_Score / Max_Raw_Score) × 100
```

### Weighted Priority Score

```python
priority_score = (
    mortality_score × 0.30 +
    community_score × 0.15 +
    egress_score × 0.20 +
    populated_score × 0.20 +
    utility_score × 0.15
)
```

---

## 📈 Results

### Priority Distribution

| Priority Class | Count | Percentage |
|----------------|:-----:|:----------:|
| 🔴 Critical | 0 | 0.0% |
| 🟠 High | 5 | 6.3% |
| 🟡 Medium | 43 | 53.8% |
| 🟢 Low | 32 | 40.0% |

### Score Statistics

| Metric | Value |
|--------|:-----:|
| Mean Priority Score | 29.37 |
| Maximum Score | 60.73 |
| Minimum Score | 8.16 |
| Standard Deviation | 13.71 |

### Top 5 Priority Zones

| Rank | Grid ID | Score | Class |
|:----:|:-------:|:-----:|:-----:|
| 1 | 163 | 60.73 | 🟠 High |
| 2 | 158 | 55.51 | 🟠 High |
| 3 | 130 | 54.48 | 🟠 High |
| 4 | 157 | 51.84 | 🟠 High |
| 5 | 162 | 50.74 | 🟠 High |

---

## 📂 Output Files

### Generated Files

The analysis generates multiple output formats for different use cases:

| File | Format | Description | Use Case |
|------|--------|-------------|----------|
| `TreeCuttingPriority_YYYYMMDD_HHMMSS.shp` | Shapefile | Timestamped spatial output | Historical reference, archiving |
| `TreeCuttingPriority_v2.shp` | Shapefile | Latest version spatial output | Current analysis, QGIS mapping |
| `TreeCuttingPriority_YYYYMMDD_HHMMSS.gpkg` | GeoPackage | Timestamped single-file format | Better than shapefile, no field name limits |
| `TreeCuttingPriority_v2.gpkg` | GeoPackage | Latest version GeoPackage | Recommended for GIS work |
| `TreeCuttingPriority.csv` | CSV | Tabular data (no geometry) | Excel analysis, reporting, statistics |
| `TreeCuttingPriority_Charts.png` | PNG | Visualization dashboard | Presentations, reports, documentation |

### Output Schema

#### Shapefile Fields (10-character limit)

| Field | Description | Data Type | Range |
|-------|-------------|-----------|:-----:|
| `Grid` | Original grid zone identifier | Integer | 1-80 |
| `mort_score` | Normalized mortality score | Float | 0-100 |
| `comm_score` | Normalized community features score | Float | 0-100 |
| `egrs_score` | Normalized egress routes score | Float | 0-100 |
| `pop_score` | Normalized populated areas score | Float | 0-100 |
| `util_score` | Normalized utility infrastructure score | Float | 0-100 |
| `priority_s` | Final weighted priority score | Float | 0-100 |
| `prior_cls` | Priority classification | String | Low/Medium/High/Critical |
| `prior_rank` | Priority rank (1 = highest priority) | Integer | 1-80 |
| `geometry` | Polygon geometry | Geometry | - |

#### GeoPackage/CSV Fields (full names)

The GeoPackage and CSV outputs include full field names for better clarity:

| Field | Full Name | Description |
|-------|-----------|-------------|
| `Grid` | Grid Zone ID | Original grid identifier |
| `mortality_score` | Tree Mortality Score | Dead/dying tree risk factor |
| `community_score` | Community Features Score | Infrastructure protection factor |
| `egress_score` | Egress Routes Score | Evacuation route protection factor |
| `populated_score` | Populated Areas Score | Residential safety factor |
| `utility_score` | Electric Utility Score | Power infrastructure factor |
| `priority_score` | Overall Priority Score | Weighted composite score |
| `priority_class` | Priority Classification | Risk category |
| `priority_rank` | Priority Rank | Numerical ranking |

---

## 🗺 Visualization

### Generated Charts

The script automatically generates a comprehensive visualization with **3 charts**:

1. **Bar Chart**: Number of grid zones per priority class
   - Shows distribution across Critical, High, Medium, and Low categories
   - Color-coded bars with value labels
   - Grid lines for easier reading

2. **Pie Chart**: Percentage distribution of priority classes
   - Visual breakdown of zone percentages
   - Color-matched with priority classes
   - Legend showing zone counts

3. **Horizontal Bar Chart**: Top 10 highest priority zones
   - Identifies specific grid zones requiring immediate attention
   - Shows priority scores and classifications
   - Color-coded by priority class

All charts are saved as a single high-resolution image (300 DPI) in [output/TreeCuttingPriority_Charts.png](output/TreeCuttingPriority_Charts.png)

### QGIS Integration

#### Method 1: Quick Load

1. Open QGIS
2. Drag and drop `TreeCuttingPriority_v2.gpkg` or `TreeCuttingPriority_v2.shp`
3. The layer will display with default styling

#### Method 2: Styled Visualization

To visualize with professional priority colors:

1. Load `TreeCuttingPriority_v2.shp` or `.gpkg`
2. Right-click layer → **Properties** → **Symbology**
3. Select **Categorized**
4. Set **Value** to `prior_cls`
5. Click **Classify**
6. Apply custom colors:

| Priority Class | Hex Color | RGB |
|----------------|-----------|-----|
| 🔴 Critical | `#E53935` | (229, 57, 53) |
| 🟠 High | `#FB8C00` | (251, 140, 0) |
| 🟡 Medium | `#FDD835` | (253, 216, 53) |
| 🟢 Low | `#43A047` | (67, 160, 71) |

7. Adjust transparency: Set **Layer Opacity** to 70% for better base map visibility
8. Add labels (optional): Enable labels using `Grid` field for zone identification

### Visual Outputs

Additional visualizations are available in the [visual-outputs/](visual-outputs/) folder:

- `layers-names.png`: Reference for all input layer names
- `layers-visual.png`: Visual overview of spatial layers

---

## 🔧 Configuration

### Adjusting Data Paths

Update the paths in [tree_cutting_priority.py](tree_cutting_priority.py) to match your directory structure:

```python
# Set data directory
DATA_DIR = Path(r"C:/Users/baram/Desktop/Raster/data")
OUTPUT_DIR = Path(r"C:/Users/baram/Desktop/Raster/output")
OUTPUT_DIR.mkdir(exist_ok=True)
```

For the workspace structure, use:
```python
DATA_DIR = Path(r"C:/tree-cutting-priority/tree_data")
OUTPUT_DIR = Path(r"C:/tree-cutting-priority/output")
```

### Adjusting Factor Weights

Modify the `WEIGHTS` dictionary in [tree_cutting_priority.py](tree_cutting_priority.py) to change factor importance:

```python
WEIGHTS = {
    'mortality': 0.30,      # 30% - Tree mortality
    'community': 0.15,      # 15% - Community features
    'egress': 0.20,         # 20% - Egress routes
    'populated': 0.20,      # 20% - Populated areas
    'utility': 0.15         # 15% - Electric utilities
}
```

**Example Scenarios:**

- **High Fire Risk Focus**: Increase `mortality` to 0.40, reduce others proportionally
- **Public Safety Focus**: Increase `egress` and `populated` to 0.25 each
- **Infrastructure Focus**: Increase `utility` and `community` to 0.25 each

### Adjusting Priority Classification Thresholds

Modify the `classify_priority` function in [tree_cutting_priority.py](tree_cutting_priority.py):

```python
def classify_priority(score):
    if score >= 75:
        return 'Critical'    # Immediate action required
    elif score >= 50:
        return 'High'        # Near-term action needed
    elif score >= 25:
        return 'Medium'      # Scheduled maintenance
    else:
        return 'Low'         # Routine monitoring
```

**Alternative Classification:**

```python
def classify_priority(score):
    if score >= 80:
        return 'Critical'    # More selective critical threshold
    elif score >= 60:
        return 'High'        
    elif score >= 40:
        return 'Medium'      
    elif score >= 20:
        return 'Low'         
    else:
        return 'Very Low'    # Add new category
```

### Customizing Utility Infrastructure Weights

In [tree_cutting_priority.py](tree_cutting_priority.py), adjust the weights for different utility types:

```python
# Current weights in STEP 8
# Transmission lines: weight 3 (highest priority)
# SubTransmission: weight 2.5
# Distribution circuits: weight 2
# Substations: weight 3 (point features)
# Pole top subs: weight 2 (point features)
```

---

## 👥 Authors

- **Ameer Saleh**
- **Bara Mhana**

**Course:** Spatial Data Analysis  
**Assignment:** Homework 2 - Tree Cutting Priority Analysis  
**Institution:** [Your Institution]  
**Date:** December 2025

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **San Bernardino National Forest (SBNF)** for providing tree mortality data
- **Fire Creek Community** for infrastructure and boundary data
- **Course Instructors** for guidance and support throughout the project
- **GeoPandas Development Team** for the excellent spatial analysis library

---

## 🚀 Future Enhancements

Potential improvements for future versions:

- [ ] Add temporal analysis for tracking priority changes over time
- [ ] Implement machine learning for predictive risk modeling
- [ ] Create interactive web map using Folium or Plotly
- [ ] Add cost-benefit analysis for prioritization
- [ ] Include weather and climate data integration
- [ ] Develop automated report generation with PDF output
- [ ] Add API for real-time data updates

---

<p align="center">
  Made with ❤️ for Spatial Data Analysis<br>
  🌲 Protecting Communities, One Tree at a Time 🌲
</p>

