# Wildlife Species Risk Assessment (Mammals)

**Teamwise Project Review 3 (DO5)**  
**Team Members:** Srushti (298) · Agadh (299) · Sneh (311)

---

## 📌 Project Overview
Many mammal species are experiencing severe population declines, making targeted conservation crucial. This project develops a machine learning framework that connects **IUCN Red List** conservation status with **GBIF** georeferenced occurrence records and **WorldClim** bioclimatic variables. Using these independent ecological and environmental predictors, the models predict species vulnerability status to support proactive conservation planning.

### Core Objectives
1. **Target Preparation:** Construct a leakage-free binary classification target (`0 = Least Concern / Near Threatened`, `1 = Vulnerable / Endangered / Critically Endangered`) from IUCN Red List mammal assessments.
2. **Occurrence Mining:** Query and validate georeferenced GBIF occurrences for species using REST API endpoints with taxon rank checks.
3. **Environmental Extraction:** Aggregate bioclimatic indicators (temperature seasonality, extreme temperatures, precipitation patterns) and elevation per species range.
4. **Modeling & Benchmarking:** Train, evaluate, and benchmark:
   - **Generalized Additive Models (GAM)** (via cubic spline transformations)
   - **Bayesian Model Averaging (BMA)**
   - **Ensemble Learning** (Voting Classifier with Random Forest, Extra Trees, and HistGradientBoosting)
5. **Evaluation:** Evaluate models using Sensitivity (Recall), Species Risk Detection Rate, ROC-AUC, and Partial Dependence / Permutation Importance for ecological factor analysis.

---

## 🗂️ Repository Structure

```
├── datasets/
│   ├── gbif/               # GBIF species occurrences, verified species, and modeling datasets
│   ├── iucn/               # IUCN Red List mammal records (raw and cleaned)
│   └── worldclim/          # WorldClim bioclimatic rasters (wc2.1_10m_bio)
├── outputs/                # Evaluation plots (ROC, confusion matrices) and metrics CSVs
├── wildlife_files/         # Output figures and plots from the notebook
├── wildlife.ipynb          # Interactive Jupyter notebook with complete pipeline
├── wildlife.py             # Full executable Python pipeline script
├── wildlife.html           # Comprehensive rendered HTML project report
├── wildlife.md             # Markdown report of the complete analysis
├── .env.example            # Template for environment configuration
└── README.md               # Project documentation
```

---

## ⚙️ Setup & Requirements

### 1. Dependencies
Install the required Python packages:
```bash
pip install pandas numpy scikit-learn matplotlib seaborn requests python-dotenv rasterio
```

### 2. Environment Configuration
Create a `.env` file in the project root:
```bash
cp .env.example .env
```
Add your IUCN Red List API v4 token to `.env`:
```env
IUCN_API_KEY=your_iucn_api_token_here
```

### 3. Running the Project
- **Jupyter Notebook:** Open `wildlife.ipynb` in VS Code or Jupyter Lab.
- **Python Script:** Run the pipeline directly:
  ```bash
  python wildlife.py
  ```
- **HTML Report:** View `wildlife.html` in any web browser for the full report and visualizations.

---

## 📊 Dataset Sources
- **IUCN Red List of Threatened Species:** Mammalia taxon export & API v4 endpoint.
- **GBIF (Global Biodiversity Information Facility):** REST API for species taxonomy matching and georeferenced occurrence coordinates.
- **WorldClim v2.1:** High-resolution global bioclimatic variables (temperature, precipitation, elevation).
