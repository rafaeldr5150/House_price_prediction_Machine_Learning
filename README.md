# 🏠 King County Real Estate Valuation System

A comprehensive machine learning project for real estate price prediction and market analysis in King County, Washington. This system analyzes housing market trends, identifies key value drivers, and provides accurate price predictions using advanced machine learning techniques.

## 📋 Table of Contents
- [Project Overview](#project-overview)
- [Business Objectives](#business-objectives)
- [Dataset Description](#dataset-description)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Project Overview

This project builds a complete real estate valuation system that:
- 🔍 Analyzes the King County housing market (May 2014 - May 2015)
- 📈 Identifies the most important factors driving property values
- 🏡 Profiles premium properties and their characteristics
- 💰 Predicts property prices with high accuracy
- 📊 Provides actionable insights for buyers, sellers, and real estate professionals

### Business Questions Answered
- "How much does the price increase per additional square meter?"
- "Is the waterfront view really worth the premium?"
- "What is the impact of location (ZIP code) on property value?"
- "What differentiates a property worth $650K+ from others?"
- "Can we predict property prices with good accuracy?"

## 📊 Dataset Description

The dataset contains 21 features with one year of housing sales data:

### Key Features
- **`price`**: Sale price (prediction target)
- **`sqft_living`**: Interior living space square footage
- **`grade`**: King County construction quality grade (1-13)
- **`bathrooms`**: Number of bathrooms
- **`bedrooms`**: Number of bedrooms
- **`waterfront`**: Waterfront view (0/1)
- **`view`**: Quality of view (0-4)
- **`condition`**: Overall condition (1-5)
- **`location`**: Geographic coordinates (lat, long) and zipcode
- **`year_built`**, **`year_renovated`**: Construction and renovation years

**Dataset Size**: 21,613 properties with 21 features each

## 🛠 Methodology

### 1. Data Preprocessing & EDA
- Comprehensive exploratory data analysis
- Outlier detection using Z-score and IQR methods
- Log transformation of price to handle skewness
- Correlation analysis (Pearson & Spearman)

### 2. Feature Engineering
- **Temporal Features**: Month extraction from sale date
- **Property Age**: Modern house classification (built after 2000)
- **Renovation Status**: Binary flag for renovated properties
- **Spatial Features**: Geographic coordinates and neighborhood metrics

### 3. Machine Learning Models
Four regression models were implemented and compared:

| Model | R² Score | MAE | RMSE | Key Features |
|-------|----------|-----|------|--------------|
| **Linear Regression** | 0.698 | 0.138 | 0.183 | Baseline model |
| **Random Forest** | 0.885 | 0.081 | 0.116 | Ensemble method |
| **AdaBoost** | 0.782 | 0.111 | 0.150 | Boosting algorithm |
| **XGBoost** | **0.901** | **0.074** | **0.106** | **Best performer** |

### 4. Model Optimization
The final XGBoost model was tuned with:
- Hyperparameter optimization
- Advanced feature engineering pipeline
- ColumnTransformer for categorical encoding
- Comprehensive cross-validation

## 🔑 Key Findings

### Top Price Drivers
1. **Construction Grade** (0.67 correlation) - Highest impact on price
2. **Living Area Size** (0.70 correlation) - Square footage matters most
3. **Location Coordinates** - Geographic positioning is crucial
4. **Bathroom Count** - More valuable than bedrooms
5. **Waterfront Status** - Significant premium for water views

### Premium Property Profile
Properties valued at $650K+ typically feature:
- High construction grades (10+)
- Larger living spaces (3,000+ sqft)
- Multiple bathrooms (3+)
- Premium locations with water views
- Recent construction or major renovations

### Geographic Insights
- Highest property values cluster around waterfront areas
- Seattle metro area commands significant location premium
- Neighborhood characteristics strongly influence prices

## 💻 Installation

### Prerequisites
- Python 3.8+
- pip package manager

### Dependencies
```bash
pip install pandas numpy matplotlib seaborn plotly scipy scikit-learn xgboost joblib
```

### Quick Start
1. Clone the repository:
```bash
git clone https://github.com/yourusername/king-county-real-estate.git
cd king-county-real-estate
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Run the analysis:
```bash
python real_estate_analysis.py
```

## 🚀 Usage

### Price Prediction
```python
from prediction_utils import predict_house_price

# Example prediction
predicted_price = predict_house_price(
    bedrooms=3,
    bathrooms=2.0,
    sqft_living=1800,
    grade=8,
    waterfront=0,
    lat=47.6062,
    long=-122.3321
)

print(f"Predicted Price: ${predicted_price:,.2f}")
```

### Model Training
```python
# Train the model with custom parameters
from models import RealEstatePredictor

predictor = RealEstatePredictor()
predictor.train_model()
predictor.evaluate_performance()
```

## 📈 Results

### Model Performance Summary
- **Best Model**: XGBoost with feature engineering
- **Test R²**: 0.901 (90.1% variance explained)
- **Mean Absolute Error**: $74,000
- **Prediction Accuracy**: ±7.4% on average

### Business Impact
- **For Sellers**: Accurate pricing strategy and value optimization
- **For Buyers**: Informed purchase decisions and negotiation leverage
- **For Agents**: Data-driven market analysis and client guidance

## 📁 Project Structure

```
king-county-real-estate/
│
├── data/
│   └── king_county_houses_aa.csv
├── main.ipynb
├── README.md
└── presentation.pdf
```

## 🤝 Contributing

We welcome contributions! Please feel free to submit pull requests or open issues for:

- Additional feature engineering ideas
- Model improvements
- Data visualization enhancements
- Documentation updates

### Contribution Guidelines
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- King County Department of Assessments for providing the dataset
- Ironhacks for project guidance and framework
- The open-source community for valuable machine learning libraries

---

**⭐ If you found this project helpful, please give it a star!**

*For questions or collaboration opportunities, please open an issue or contact the project maintainers.*
