# us-college-major-roi
# U.S. College Major Employment Return Analysis
# 美国大学专业就业回报数据分析

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/qinghewang0628/us-college-major-roi/blob/main/analysis.ipynb)

## Overview | 项目简介

Exploratory data analysis (EDA) of U.S. college major salary, student debt, and AI-software job penetration, based on a Kaggle public dataset with 227,980 program-level records. The project evaluates the return on investment (ROI) across bachelor's degree fields and provides data references for students and public policy discussion.

基于 Kaggle 美国高校公开数据集（227,980 条项目记录），使用 Python 对本科毕业生薪资、学生贷款负债与 AI 软件岗位渗透率进行探索性数据分析，评估不同专业方向的投入回报（ROI），为学生选专业与公共政策讨论提供数据参考。

## Data | 数据来源

- **Source**: College Majors 2026: Earnings, Debt, Jobs, AI(https://www.kaggle.com/datasets/kylefengkfeng209/college-majors-2026-earnings-debt-jobs-ai))
- **Raw records**: 227,980 rows × 72 columns
- **Filtered to Bachelor's Degree**: 71,664 rows
- **Final analysis sample**: 22,485 rows (after dropping missing earnings / debt)

核心字段：

| Column | Description |
|---|---|
| `cip_family_title` | 专业大类 |
| `median_earnings_4yr_usd` | 毕业 4 年薪资中位数（美元） |
| `debt_to_earnings_1yr` | 毕业 1 年负债收入比 |
| `ai_software_occupation_share` | 关联岗位中使用 AI 软件的比例 |

## Methods | 方法

1. **Data Cleaning | 数据清洗**
   - Filtered `credential_name == "Bachelor's Degree"`
   - Selected 4 core fields
   - Dropped rows missing earnings or debt-to-earnings ratio
   - Result: 22,485 clean records

2. **Exploratory Analysis | 探索性分析**
   - Grouped by `cip_family_title`
   - Computed median salary, median debt-to-earnings ratio, mean AI-software share
   - Pearson correlation between AI-software share and median earnings

3. **Visualization | 可视化**
   - Horizontal bar chart: Top 15 highest-earning major fields
   - Scatter plot: Earnings vs. debt-to-earnings ratio
   - Scatter plot: AI-software share vs. earnings

4. **ROI Segmentation | 回报分层**
   - High ROI: earnings > $85,000 and debt ratio < 0.4
   - High burden: earnings < $50,000 and debt ratio > 0.8

## Key Findings | 核心发现

- **Overall**: median 4-year earnings = **$60,180**; median debt-to-earnings ratio = **0.55**.
- **Top-earning fields**: Military Science ($103,706), Engineering ($93,873), Construction Trades ($90,691), Computer and Information Sciences ($87,413).
- **High ROI fields**: Military Science, Engineering, Construction Trades, Computer and Information Sciences.
- **High debt burden fields**: Precision Production (1.39), Communications Technologies (1.01), Visual and Performing Arts (0.92), Library Science (0.87).
- **AI-software share vs. earnings**: Pearson correlation = **0.435**, a moderate positive relationship. Majors linked to AI-using occupations tend to have higher salaries.
- **Polarization**: returns across majors are strongly polarized — some fields combine high salary with low debt, others combine low salary with high debt.

## Files | 文件结构

```text
us-college-major-roi/
├── analysis.ipynb                # Main notebook
├── cleaned_bachelor_data.csv     # Cleaned dataset
├── requirements.txt
├── README.md
└── images/
    ├── 01_top_salary_majors.png
    ├── 02_earnings_vs_debt.png
    └── 03_ai_vs_salary.png
```

## How to Run | 运行方式

### Option 1: Google Colab (Recommended)
Click the badge at the top, or upload `analysis.ipynb` to [colab.research.google.com](https://colab.research.google.com).

### Option 2: Local Jupyter
1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Launch the notebook:
```bash
jupyter notebook analysis.ipynb
```

### requirements.txt
```text
pandas
numpy
matplotlib
seaborn
jupyter
```
