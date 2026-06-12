# Exploratory Data Analysis - Detailed Breakdown

## Overview

This document outlines the comprehensive EDA (Exploratory Data Analysis) performed on the student performance dataset.

---

## 1. Data Overview & Structure

### Dataset Dimensions
- **Rows**: 395 students
- **Columns**: 33 features
- **Missing Values**: 0 (100% complete)
- **Memory Usage**: ~102 KB

### Data Types
- **Numeric Features**: 16 (int64)
- **Categorical Features**: 17 (object/string)

---

## 2. Univariate Analysis

### Numerical Features Analysis

#### Central Tendency
- **Mean Age**: 16.7 years
- **Mean Final Grade (G3)**: 10.42/20
- **Mean Study Time**: 2.04 hours

#### Dispersion
- **Age Std Dev**: 1.28 (very uniform age group)
- **Grade Std Dev**: 4.58 (moderate variation)
- **Failure Std Dev**: 0.74 (most students have 0-1 failures)

#### Range Analysis
| Feature | Min | Max | Q1 | Median | Q3 |
|---------|-----|-----|-----|--------|-----|
| Age | 15 | 22 | 16 | 17 | 18 |
| G3 (Final Grade) | 0 | 20 | 8 | 11 | 14 |
| Study Time | 1 | 4 | 1 | 2 | 2 |
| Failures | 0 | 3 | 0 | 0 | 0 |
| Absences | 0 | 75 | 0 | 4 | 8 |

### Categorical Features Analysis

#### Gender Distribution
- Female (F): ~50%
- Male (M): ~50%

#### School Type
- GP (Gabriel Pereira): Majority
- MS (Mousinho da Silveira): Minority

#### Address Type
- Urban (U): Majority
- Rural (R): Minority

#### Family Size
- Greater than 3 (GT3): ~71%
- Less than or equal to 3 (LE3): ~29%

#### Parental Status
- Cohabiting (T): ~58%
- Apart (A): ~42%

---

## 3. Bivariate Analysis

### Correlation with Target (G3 - Final Grade)

#### Strong Positive Correlations (r > 0.7)
- **G2 (Period 2 Grade)**: 0.90 ⭐ (Strongest predictor)
- **G1 (Period 1 Grade)**: 0.80 ⭐ (Very strong)

#### Moderate Positive Correlations (0.1 < r < 0.7)
- **Mother's Education (Medu)**: 0.22
- **Father's Education (Fedu)**: 0.15
- **Study Time**: 0.10

#### Weak Correlations (|r| < 0.1)
- **Family Relationships**: 0.05
- **Absences**: 0.03
- **Free Time**: 0.01

#### Negative Correlations (r < 0)
- **Past Failures**: -0.36 (Important risk factor)
- **Age**: -0.16
- **Going Out**: -0.13
- **Travel Time**: -0.12
- **Weekend Alcohol**: -0.05
- **Weekday Alcohol**: -0.05
- **Health**: -0.06

---

## 4. Distribution Analysis

### Final Grade (G3) Distribution
- **Bimodal Pattern**: Peaks around 0 and 10-11
- **Right-Skewed**: More lower grades than upper
- **Outliers**: 38 students with 0 grade (complete failure)
- **Most Common**: Grades 10-11 (103 students combined)

### Grade Progression
- **G1 Mean**: 10.91/20
- **G2 Mean**: 10.71/20  
- **G3 Mean**: 10.42/20
- **Trend**: Slight decline through periods

---

## 5. Group Comparisons

### By Gender
- Females typically score slightly higher
- Similar distribution patterns

### By School Type
- Performance varies by school
- School type shows moderate effect

### By Family Size
- Larger families: Mixed results
- Family support more important than size

### By Parental Status
- Cohabiting parents: Slight advantage
- Apart parents: More variation

### By Address Type (Urban/Rural)
- Urban students: Slightly better performance
- Rural: More variation

---

## 6. Feature Relationships

### Strong Multicollinearity
- G1-G2-G3 highly correlated (academic momentum)
- Mother's & Father's education correlated

### Interesting Interactions
- Study time effect varies by family support
- Failures impact varies by parent education
- Age shows non-linear relationships

---

## 7. Outliers & Anomalies

### Identified Patterns
1. **Complete Failures**: 38 students (9.6%) with G3=0
   - May indicate dropouts or non-engagement
   - Different pattern from regular low performers

2. **High Achievers**: 10 students (2.5%) with G3=18-20
   - Consistent high performance
   - High study time
   - Fewer failures

3. **Absence Outliers**: Some students with 75 absences
   - Extreme outlier
   - Likely indicates dropout
   - Correlates with low grades

---

## 8. Data Quality Assessment

✅ **Strengths**
- No missing values
- Consistent data types
- Reasonable ranges for most features
- Good sample size (395 records)

⚠️ **Considerations**
- Extreme absences (0-75) suggest data errors or dropouts
- Bimodal grade distribution unusual
- Age range narrow (15-22)
- Imbalanced target distribution

---

## 9. Key Insights Summary

### Primary Findings
1. **Previous performance is destiny**: G1 and G2 are the best predictors
2. **Failures have major impact**: -0.36 correlation is significant
3. **Family education matters**: Parental education positively influences
4. **Data is clean but biased**: No missing values but 10% complete failures
5. **Academic momentum exists**: Grades decline slightly through year

### Actionable Insights
1. **Early intervention**: Help with Period 1 grades
2. **Failure prevention**: Track and support students with prior failures
3. **Family involvement**: Encourage parental engagement
4. **Identify at-risk**: Monitor absences and early performance

---

## 10. Recommendations for Next Stages

### For Stage 3 (Preprocessing)
- Handle the 38 zero-grade outliers carefully
- Consider binning or transformation for skewed features
- Address extreme absence values
- Scale numerical features for ML algorithms

### For Stage 4 (Feature Engineering)
- Create interaction features between key variables
- Engineer features from categorical variables
- Consider lag features for grade progression
- Combine related features (e.g., parent education average)

### For Stage 5 (Modeling)
- Use G1 and G2 as strong baseline features
- Consider two-class classification: Pass/Fail vs Regression
- Handle class imbalance in complete failures
- Use feature importance to validate findings

---

## Files Generated

- `correlation_heatmap.png` - Correlation matrix visualization
- `grade_distribution.png` - Final grade distribution
- `feature_distributions.png` - All numerical features
- `student_demographics.png` - Demographic analysis
- `academic_factors.png` - Academic feature analysis
- `lifestyle_factors.png` - Lifestyle feature analysis

---

**Analysis Date**: June 2026
**Analyst**: ksunitareddy1-cyber
**Status**: Complete - Ready for Stage 3
