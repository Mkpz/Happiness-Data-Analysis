# World Happiness Trends Analysis (2007-2017)

[![R](https://img.shields.io/badge/R-276DC3?style=flat&logo=r&logoColor=white)](https://www.r-project.org/)
[![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Random%20Forest-green)](https://github.com/Mkpz/Happiness-Data-Analysis)
[![Data Visualization](https://img.shields.io/badge/Data-Visualization-blue)](https://github.com/Mkpz/Happiness-Data-Analysis)
[![Statistical Analysis](https://img.shields.io/badge/Statistical-Analysis-orange)](https://github.com/Mkpz/Happiness-Data-Analysis)
[![Geospatial Analysis](https://img.shields.io/badge/Geospatial-Analysis-red)](https://github.com/Mkpz/Happiness-Data-Analysis)
[![Cross Validation](https://img.shields.io/badge/Cross-Validation-purple)](https://github.com/Mkpz/Happiness-Data-Analysis)

A comprehensive machine learning analysis examining global happiness trends over time, implementing Random Forest regression to predict happiness scores based on socioeconomic indicators with 0.47 RMSE on validation data.

## Project Overview

This project analyzes the World Happiness Report dataset spanning 2007-2017, exploring how economic, social, and political factors influence well-being across 150+ countries. Using advanced machine learning techniques and extensive exploratory data analysis, the project achieves accurate happiness score predictions while identifying key drivers of life satisfaction globally.

### Key Findings

- GDP per capita (32%), life expectancy (28%), and social support (25%) are the most influential predictors of happiness
- Regional disparities: Western Europe and North America consistently score above 7.5, while Sub-Saharan Africa scores below 3.5
- Temporal trends: Eastern Europe showed significant improvements (0.5+ unit increases from 2007-2017)
- Strong correlations: Log GDP per capita (0.785), social support (0.699), and life expectancy (0.707) with happiness

## Objectives

1. Analyze happiness trends across countries and regions over a decade
2. Identify socioeconomic factors most strongly associated with happiness
3. Build predictive models to forecast happiness scores using machine learning
4. Visualize global patterns and temporal changes through choropleth maps

## Repository Structure

```
happiness-data-analysis/
│
├── Happiness Analysis Regression Project Code.Rmd    # R Markdown analysis code with ML models
├── Happiness Analysis Regression Project Report.pdf  # Comprehensive project report
├── .gitattributes                                    # Git LFS configuration
└── README.md                                         # Project documentation
```

**Note**: The dataset used in this analysis is proprietary/locally stored and not included in this repository.

## Getting Started

### Prerequisites

```r
# Required R version
R >= 4.0.0

# Install required packages
install.packages(c("randomForest", "caret", "ggplot2", "dplyr", 
                   "maps", "ggmap", "corrplot"))
```

### Running the Analysis

1. Clone the repository:
```bash
git clone https://github.com/yourusername/happiness-data-analysis.git
cd happiness-data-analysis
```

2. Obtain the dataset:
   - The analysis uses World Happiness Report data (2007-2017)
   - Dataset is not publicly available in this repository
   - Ensure you have access to the required dataset locally

3. Configure data path:
```r
# Update the data path in the R Markdown file to point to your local dataset
# Modify the file path in: Happiness Analysis Regression Project Code.Rmd
```

4. Run the analysis:
```r
# In R or RStudio
# Open and knit the R Markdown file
rmarkdown::render("Happiness Analysis Regression Project Code.Rmd")

# Or run interactively in RStudio
# File -> Open -> Happiness Analysis Regression Project Code.Rmd
# Click "Knit" button
```

## Dataset Information

**Source**: World Happiness Report (2007-2017)  
**Observations**: 1,500+ country-year records  
**Countries**: 150+ nations  

**Key Variables**:
- `happiness_score`: Self-reported life satisfaction (0-10 scale)
- `log_gdp_per_capita`: Economic prosperity indicator
- `social_support`: Family and friend networks
- `life_expectancy`: Healthy life expectancy at birth
- `freedom_choices`: Perception of life autonomy
- `corruption`: Perceived corruption in government/business
- `positive_affect`: Frequency of positive emotions

## Technologies & Methods

### Programming & Tools
- **Language**: R
- **Key Packages**:
  - `randomForest` - Random Forest regression
  - `caret` - Model training and hyperparameter tuning
  - `ggplot2` - Data visualization
  - `dplyr` - Data manipulation
  - `maps` / `ggmap` - Choropleth maps

### Machine Learning Approach

**Random Forest Regression Model**

The final model aggregates predictions from multiple decision trees:

```
happiness = f(log GDP per capita, social support, life expectancy, 
              freedom of choice, corruption, positive affect)
```

**Mathematical representation**:
```
ŷ = (1/T) * Σ(t=1 to T) h_t(X)
```
where:
- ŷ = predicted happiness score
- T = total number of trees
- h_t(X) = prediction from tree t given features X

### Model Performance

**Validation RMSE**: 0.4711557
- Predictions are off by ~0.47 units on average from true happiness scores
- Strong predictive accuracy on unseen data

## Model Details

### Hyperparameter Tuning

**Grid Search Parameters**:
- `ntree`: Number of trees in forest (controls variance vs. computational cost)
- `mtry`: Number of predictors sampled at each split (controls randomness)

**Cross-Validation**:
- 5-fold CV for hyperparameter selection
- 10-fold CV for final model training (maximized data usage)
- Consistent performance across folds (demonstrates generalizability)

### Variable Importance Rankings

| Predictor | Importance (%) |
|-----------|----------------|
| Log GDP per capita | 32% |
| Life expectancy | 28% |
| Social support | 25% |
| Freedom of choice | ~8% |
| Corruption | ~5% |
| Positive affect | ~2% |

## Key Analyses

### 1. Exploratory Data Analysis

**Correlation Analysis**:
- Strong positive relationships between happiness and:
  - Log GDP per capita: 0.785
  - Social support: 0.699
  - Life expectancy: 0.707
- Life expectancy ↔ GDP per capita: 0.806 (highly interconnected)
- Corruption ↔ Freedom: -0.481 (governance impacts happiness)

### 2. Temporal Trends (2007-2017)

**Consistent High Performers**:
- Canada: Maintained scores above 7.0 (strong social support, economic stability)
- Scandinavian countries: Denmark, Finland, Norway (>7.5)

**Improving Nations**:
- Bolivia: Rose from 5.5 → 6.0 (social/economic progress)
- Portugal: Climbed 5.0 → 6.0 (post-recession recovery)
- Eastern Europe: Poland, Hungary (+0.5 units)

**Declining Nations**:
- Egypt: Dropped 5.0 → 4.5 (Arab Spring instability)
- Yemen: Remained below 3.5, declining post-2014 (ongoing conflict)
- Italy: Slight decline 6.5 → 6.0 (economic challenges)

### 3. Regional Patterns

- Europe & Americas: Outperformed other regions consistently
- Sub-Saharan Africa: Lagged behind (scores <3.5)
- Conflict zones: Yemen, Afghanistan showed lowest scores
- Socioeconomic stability: Critical role in happiness trends

---

**Note**: This analysis represents academic coursework demonstrating proficiency in machine learning, statistical modeling, and data visualization using R.
