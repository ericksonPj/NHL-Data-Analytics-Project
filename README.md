# NHL Player Demographics & Statistical Analysis

A comprehensive statistical analysis of the 2022-23 NHL player roster examining physical attributes, nationality distribution, and position-specific characteristics using R and advanced statistical methods.

**🔗 Live Project:** [View Full Analysis](https://ericksonpj.github.io/NHL-Data-Analytics-Project/)

---

## 📊 Project Overview

This project analyzes the demographic and physical characteristics of NHL players to understand:
- How team rosters are structured across different positions
- Regional representation in professional hockey
- Physical attribute requirements for different player roles
- Statistical distributions and sampling methodologies in sports analytics

### Key Questions Answered
- What are the typical physical characteristics (height/weight) of NHL players by position?
- How does nationality and region affect player distribution in the league?
- Do different positions require distinct physical profiles?
- How do sampling methods perform on categorical sports data?

---

## 🛠️ Technical Stack

**Language & Libraries:**
- **R** - Primary analysis language
- **Plotly** - Interactive data visualizations
- **dplyr/tidyr** - Data manipulation and transformation
- **ggplot2** - Static visualizations

**Statistical Methods:**
- Central Limit Theorem (CLT) analysis
- Probability distributions (normal, sampling distributions)
- Sampling techniques (Simple Random, Stratified, Systematic)
- Descriptive statistics and hypothesis testing

**Data Source:**
- Kaggle NHL Player Dataset (2022-23 season)
- 2,941 player records after preprocessing

---

## 🔍 Key Findings

### Physical Characteristics
- **Average Height:** 73 inches (6'1") with ±2 inch standard deviation
- **Average Weight:** 199 lbs with normal distribution (σ = 16.1 lbs)
- **Position Differences:**
  - Defensemen & Goalies: Tallest positions (importance of reach)
  - Forwards: Lighter and more agile (emphasis on speed)
  - Goalies: Tall but lean (balance of reach and agility)

### Geographic Distribution
- **North American Dominance:** Canada (45.8%) and USA (25.7%) represent 71.5% of players
- **European Presence:** Sweden, Finland, Russia, Czech Republic account for 22.7%
- **Top 10 Countries:** Comprise 95%+ of the NHL player population

### Statistical Insights
- Height and weight distributions closely follow normal distribution
- Sampling distribution demonstrates Central Limit Theorem validity
- Stratified sampling performs best for position-based categorical data
- Missing data (3%) had minimal impact on overall analysis

---

## 📈 Methodology

### 1. Data Preprocessing
- **Data Cleaning:**
  - Converted position codes to full names (C → Center, RW → Right Wing, etc.)
  - Transformed height from character strings to numeric (inches)
  - Created regional grouping variable for geographic analysis
  - Handled 93 missing values (3% of dataset) as NA

- **Feature Engineering:**
  - Region classification (North America, Europe, Russia)
  - Position grouping (Forward, Defenseman, Goalie)
  - Standardized nationality codes (ISO 3-letter format)

### 2. Statistical Analysis
- **Descriptive Statistics:** Mean, median, standard deviation, quartiles
- **Distribution Analysis:** Histograms, density plots, Q-Q plots
- **Central Limit Theorem:** Demonstrated with sampling distributions of varying sizes (n=5, 15, 30, 60)
- **Comparative Analysis:** Position-based and region-based groupings

### 3. Sampling Methods Evaluation
Compared three sampling approaches:
- **Simple Random Sampling (SRS):** Without replacement, uniform probability
- **Stratified Sampling:** Proportional allocation by position
- **Systematic Sampling:** Every kth observation selected

**Finding:** Stratified sampling provided best representation for categorical position data while maintaining subgroup proportions.

### 4. Visualization Strategy
- Interactive Plotly charts for exploratory analysis
- Comparative visualizations (box plots, grouped bar charts)
- Distribution overlays showing theoretical vs. actual distributions
- Position and region faceted analyses

---

## 📁 Project Structure

```
NHL-Data-Analytics-Project/
├── data/
│   └── nhl_rosters.csv              # Source data from Kaggle
├── analysis/
│   ├── preprocessing.R              # Data cleaning and transformation
│   ├── exploratory_analysis.R       # Descriptive statistics
│   ├── sampling_methods.R           # CLT and sampling demonstrations
│   └── visualizations.R             # Plotly interactive charts
├── docs/
│   └── index.html                   # Published analysis report
└── README.md                        # This file
```

---

## 🎯 Key Technical Demonstrations

### Central Limit Theorem Implementation
```r
# Demonstrated CLT with varying sample sizes
sample_sizes <- c(5, 15, 30, 60)
sampling_distribution <- map(sample_sizes, ~{
  replicate(1000, mean(sample(height, .x, replace = FALSE)))
})
# Result: As n increases, distribution approaches normality
```

### Stratified Sampling for Categorical Data
```r
# Position-based stratification
stratified_sample <- roster_data %>%
  group_by(position) %>%
  sample_frac(size = 0.1) %>%
  ungroup()
# Maintains exact position proportions in sample
```

### Interactive Visualization with Plotly
```r
plot_ly(data = nhl_data, x = ~position, y = ~height, 
        type = "box", color = ~region) %>%
  layout(title = "Height Distribution by Position and Region")
```

---

## 💡 Insights & Implications

### For Team Building
- Position-specific recruiting should consider physical profiles
- Forward positions can optimize for speed/agility over size
- Defensive positions benefit from height/reach advantages

### Statistical Learning
- Real-world demonstration of CLT validity in sports data
- Sampling method selection impacts categorical data representation
- Normal distributions appear naturally in biological measurements

### Future Enhancements
- Incorporate performance statistics (goals, assists, +/-)
- Longitudinal analysis tracking physical attribute trends over decades
- Predictive modeling for draft prospect evaluation
- Advanced metrics correlation with physical characteristics

---

## 🚀 Skills Demonstrated

**Statistical Analysis:**
- Hypothesis testing and inferential statistics
- Distribution analysis and probability theory
- Sampling methodology and experimental design
- Data normalization and standardization

**Data Manipulation:**
- ETL processes (Extract, Transform, Load)
- Missing data handling strategies
- Categorical variable encoding
- Feature engineering for analysis

**Data Visualization:**
- Interactive dashboard creation
- Multi-dimensional comparative analysis
- Statistical distribution visualization
- Storytelling through data

**Programming:**
- R for statistical computing
- Functional programming with `purrr`
- Tidyverse ecosystem proficiency
- Reproducible research practices

---

## 📝 Conclusion

This analysis reveals that while the NHL maintains diverse international representation, North America dominates the player pool, with the top 10 countries accounting for over 95% of NHL players. Physical characteristics show clear position-specific patterns, with defenseman and goalie performance focused on size and reach, while center and wing positions are related to agility and speed.

The project successfully demonstrates application of statistical theory (Central Limit Theorem) to real-world sports data, validates multiple sampling methodologies, and provides actionable insights into roster construction and player development.

**Key Takeaway:** Trends in professional hockey are showing prioritization for smaller players with high agility and dynamic scoring ability, suggesting the sport is evolving toward speed-based gameplay over traditional size advantages.

---

## 👤 Author

**Pete Erickson**  
MS in Applied Data Analytics (AI/ML) - Boston University  
[GitHub](https://github.com/ericksonpj)

---

## 📄 License

This project is available for educational and portfolio purposes. Data sourced from Kaggle under their respective terms of use.

---

## 🙏 Acknowledgments

- **Data Source:** Kaggle NHL Dataset
- **Statistical Methods:** Inspired by coursework in research methodology and statistical analysis
- **Visualization Tools:** R community (Plotly, ggplot2, tidyverse contributors)
