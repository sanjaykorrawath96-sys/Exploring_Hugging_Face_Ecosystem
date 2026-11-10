# Exploring_Hugging_Face_Ecosystem

# Hugging Face AI Models – Web Scraping and Exploratory Data Analysis

## Project Overview

The AI ecosystem is growing rapidly, with thousands of models being published on platforms such as Hugging Face. Finding the right model can be challenging because models differ in their capabilities, supported frameworks, languages, licenses, popularity, and community engagement.

This project uses **Python and Selenium WebDriver** to automate the collection of AI model metadata from Hugging Face. The collected information is organized into a structured dataset, cleaned using Pandas, and analyzed through Exploratory Data Analysis (EDA) and statistical hypothesis testing.

The goal is to understand model popularity, downloads, frameworks, pipeline categories, licensing, and community engagement to support more informed AI model selection.

## Business Problem

Developers, businesses, and researchers often need to compare AI models before selecting one for a project. Manually visiting individual model pages to collect and compare information is time-consuming.

The lack of a centralized, analysis-ready comparison dataset makes it difficult to evaluate models based on popularity, supported technologies, licensing, and community activity. This project addresses the problem by automating metadata collection and analyzing the resulting dataset.

## Project Objectives

- Automate AI model data collection from Hugging Face using Selenium.
- Collect model metadata and store it in a structured CSV dataset.
- Clean and preprocess the collected data.
- Perform univariate, bivariate, and multivariate analysis.
- Visualize model popularity and community engagement.
- Conduct statistical hypothesis tests.
- Generate insights that can support AI model discovery and selection.

## Technologies and Libraries

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Selenium | Browser automation and web scraping |
| Chrome WebDriver | Automating browser interactions |
| Pandas | Data collection, manipulation, and cleaning |
| NumPy | Handling numerical values and missing data |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualizations |
| SciPy | Statistical hypothesis testing |
| Jupyter Notebook | Development and analysis environment |

## Data Collection

The project uses Selenium WebDriver to access Hugging Face and collect model information.

### Data Collection Workflow

1. Open the Hugging Face website using Selenium.
2. Navigate to the Models section.
3. Browse trending model listings across multiple pages.
4. Collect model page URLs, targeting up to 500 model pages.
5. Visit individual model pages.
6. Extract relevant metadata using XPath and CSS selectors.
7. Store the extracted records in a Pandas DataFrame.
8. Export the dataset as a CSV file.

### Dataset Features

The following attributes are collected from the model pages:

| Column | Description |
|---|---|
| Model_Name | Name of the AI model |
| Author | Model creator or organization |
| Pipeline_Tag | Model task or pipeline category |
| Framework | Associated framework or library |
| Weight_Format | Model weight format |
| Language | Supported language information |
| License | Model license information |
| Research_Paper | Associated research paper information |
| Like_Count | Number of likes received by the model |
| Follower_Count | Author or repository follower count |
| Downloads_Last_Month | Model downloads during the last month |
| Community_Posts | Number of community discussion posts |
| Model_URL | URL of the model page |

**Note:** The notebook targets up to 500 model pages. The actual number of successfully collected records may vary depending on website availability, page structure, and scraping execution.

## Data Cleaning and Preprocessing

The collected data is processed before performing analysis.

Key preprocessing operations include:

- Removing records with missing model names.
- Replacing missing author values with `Unknown`.
- Replacing missing pipeline tags and frameworks with `unknown`.
- Handling missing weight formats and license information.
- Replacing missing follower counts with `0`.
- Replacing missing download counts with `0`.
- Handling missing community post counts.
- Converting numerical engagement columns into numeric data types.
- Checking missing values and dataset information.

The `Research_Paper` column is dropped in the initial cleaning workflow.

## Exploratory Data Analysis (EDA)

The project performs three levels of exploratory analysis.

### 1. Univariate Analysis

Analyzes individual variables to understand their distributions and patterns.

Visualizations include:

- Distribution of model downloads.
- Distribution of model likes.
- Top 10 pipeline tags.
- Framework distribution.
- Language distribution.

### 2. Bivariate Analysis

Examines relationships between two variables.

Analysis includes:

- Downloads vs. Like Count.
- Pipeline Tag vs. Like Count.
- Author vs. Downloads (Top 10 Authors).
- License distribution by framework.

Visualizations include scatter plots, box plots, bar charts, and cross-tabulations.

### 3. Multivariate Analysis

Explores relationships among multiple numerical and categorical variables.

Analysis includes:

- Correlation matrix.
- Correlation heatmap.
- Pairplot for downloads, likes, and followers.
- Framework vs. Pipeline Tag cross-tabulation heatmap.

## Statistical Hypothesis Testing

Three statistical tests are performed to investigate relationships and differences in the collected data.

### 1. Independent Two-Sample t-Test

**Business Question:** Do Transformer models receive more downloads than PyTorch models?

- **Null Hypothesis (H₀):** The mean downloads of Transformer and PyTorch models are equal.
- **Alternative Hypothesis (H₁):** The mean downloads are different.

Python library: `scipy.stats.ttest_ind`

### 2. One-Way ANOVA

**Business Question:** Do average downloads differ across different pipeline tags?

- **Null Hypothesis (H₀):** All pipeline tags have the same mean downloads.
- **Alternative Hypothesis (H₁):** At least one pipeline tag has a different mean.

Python library: `scipy.stats.f_oneway`

### 3. Chi-Square Test of Independence

**Business Question:** Is the framework associated with the pipeline tag?

- **Null Hypothesis (H₀):** Framework and Pipeline_Tag are independent.
- **Alternative Hypothesis (H₁):** Framework and Pipeline_Tag are associated.

Python library: `scipy.stats.chi2_contingency`

**Significance level:** 0.05

The p-value is compared with 0.05 to determine whether to reject or fail to reject the null hypothesis.

## Project Workflow

```text
Hugging Face Website
        |
        v
Selenium Web Scraping
        |
        v
Collect Model Metadata
        |
        v
Pandas DataFrame
        |
        v
Export Dataset to CSV
        |
        v
Data Cleaning & Preprocessing
        |
        v
Exploratory Data Analysis
        |
        +----------------------+
        |          |           |
        v          v           v
    Univariate  Bivariate  Multivariate
     Analysis   Analysis    Analysis
        |          |           |
        +----------+-----------+
                   |
                   v
          Hypothesis Testing
                   |
                   v
             Insights
```

## Repository Structure

```text
Hugging-Face-Web-Scraping/
│
├── Web Scrapping-Hugging-Face.ipynb
├── huggingface_models.csv
├── README.md
└── requirements.txt
```

*The CSV file and requirements file should be added to the repository if you choose to publish them.*

## Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/Hugging-Face-Web-Scraping.git
```

### 2. Navigate to the Project Folder

```bash
cd Hugging-Face-Web-Scraping
```

### 3. Install Required Libraries

```bash
pip install pandas numpy selenium matplotlib seaborn scipy jupyter
```

Alternatively, install dependencies using:

```bash
pip install -r requirements.txt
```

### 4. Set Up Chrome WebDriver

- Install Google Chrome.
- Ensure Selenium can access a compatible ChromeDriver.
- Configure the browser environment if required by your system.

Recent Selenium versions can manage compatible drivers through Selenium Manager in supported environments.

### 5. Run the Jupyter Notebook

```bash
jupyter notebook
```

Open `Web Scrapping-Hugging-Face.ipynb` and execute the cells in sequence.

## Key Outcomes

This project creates a structured dataset of Hugging Face model metadata and demonstrates how web scraping can be combined with data analysis and statistical testing.

The analysis is designed to help investigate:

- Which pipeline categories are most represented.
- How downloads and likes are distributed.
- Which authors have high total downloads.
- How frameworks and licenses are distributed.
- Whether downloads differ across selected framework groups and pipeline categories.
- Whether framework and pipeline tag are statistically associated.

Actual findings and statistical conclusions should be added here after running the notebook and reviewing its outputs.

## Skills Demonstrated

- Python Programming
- Web Scraping and Browser Automation
- Selenium WebDriver
- Data Extraction
- Data Cleaning and Preprocessing
- Exploratory Data Analysis (EDA)
- Univariate, Bivariate, and Multivariate Analysis
- Data Visualization
- Statistical Hypothesis Testing
- Data Interpretation

## Limitations and Considerations

- Hugging Face page layouts and HTML selectors may change, requiring updates to the scraping code.
- The number of successfully scraped models depends on website availability and execution.
- Missing or unavailable metadata may affect comparisons.
- Missing numerical values replaced with zero should be interpreted carefully.
- The statistical tests depend on their assumptions and on the quality and representativeness of the scraped data.
- The scraped information represents a snapshot at the time of collection; downloads, likes, and other engagement metrics can change.

## Conclusion

This project demonstrates an end-to-end workflow for collecting, cleaning, exploring, and statistically analyzing AI model metadata from Hugging Face.

By combining Selenium-based web scraping with Python data analysis libraries, the project transforms information from individual model pages into a structured dataset that can be used to explore model popularity, technical characteristics, and community engagement.

---

**Project:** Hugging Face AI Models – Web Scraping and EDA  
**Platform:** Hugging Face  
**Language:** Python
