---
title: "Exploring Sentiment and Content Patterns in News Articles"
date: 2025-10-25
---

<link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}">

## Project Overview

News media plays a significant role in shaping public perception, particularly when reporting on countries or communities that readers may be unfamiliar with. This project explores whether **systematic differences** exist in the *sentiment* and *language* used when news articles mention different groups of people.

Rather than focusing on individual bias labels (which are difficult to define and annotate), we adopted a **data-driven linguistic analysis** approach to examine:

- How sentiment and emotion vary across groups
- What topics and phrases are most commonly associated with those groups
- Whether potentially vulnerable groups are disproportionately linked to negative content

---

## Research Questions

This project is guided by the following questions:

- **Do news articles use different sentiment or emotional framing when discussing different groups?**
- **Does the content (topics and phrases) vary systematically across groups?**
- **Can these patterns be detected using NLP techniques such as Named Entity Recognition and sentiment analysis?**

---

## Defining Groups

Identifying “vulnerable groups” directly from text is challenging and subjective. Instead, we use an **external, standardized proxy**:

### World Bank Income Classification (2024)

Countries are grouped into four income levels:
- **Low income**
- **Lower-middle income**
- **Upper-middle income**
- **High income**

We assume that countries in lower income groups may be *more vulnerable* to harmful or sensationalized framing, and we analyze whether this is reflected in news language.

All entities extracted from news headlines are mapped to these income groups based on country-level information.

---

## Datasets

We combine multiple large-scale news datasets to maximize coverage:

| Dataset        | Articles |
|---------------|----------|
| Global News   | 933,257  |
| Huffington Post | 209,527 |
| Webhose       | 100,476  |
| BBC           | 42,329   |

Due to missing article bodies and the infeasibility of large-scale scraping, **our analysis is performed on news headlines only**.

---

## Data Preprocessing

The following preprocessing steps were applied:

- Removed duplicate headlines
- Dropped articles with missing titles
- Filtered out non-English headlines using character-based heuristics
- Converted text to lowercase and removed punctuation
- Retained only relevant fields (headline, date, category)

For the Webhose dataset, thousands of JSON files were converted into a unified CSV format.

---

## Methodology

Since the data does **not contain labels** such as “biased” or “unbiased”, we do not train a supervised model. Instead, we extract and analyze **linguistic features**.

### 1. Named Entity Recognition (NER)

We use **spaCy’s `en_core_web_trf` transformer-based model** to extract entities from headlines.

From the available entity labels, we focus on:
- **GPE** (countries, cities)
- **NORP** (nationalities, religious or political groups)
- **PERSON**

Entities are mapped to income groups using World Bank country classifications.

---

### 2️. Emotion Classification

To go beyond simple positive/negative sentiment, we apply a **pretrained emotion classifier** from HuggingFace.

Each headline is assigned an emotion label (e.g., neutral, fear, anger, joy), and emotion distributions are aggregated by income group.

---

### 3. Content Analysis (Words & Phrases)

To understand *what* is being discussed:

- Stopwords are removed
- Place names are excluded to avoid trivial correlations
- We extract **unigrams, bigrams, and trigrams**
- **TF–IDF weighting** is applied to highlight phrases that are uniquely associated with each income group

The results are visualized using word clouds.

---

## Results

### Emotion Distribution by Income Group (Dataset 1)

![Emotion Distribution across Groups](https://raw.githubusercontent.com/Rtf13/Sentiment-analysis-blog/main/assets/images/emotion_distribution_by_group.png)

Across all income groups, the majority of headlines are classified as **neutral**.  
No group shows a disproportionately high level of negative emotion.

---

### Emotion Distribution by Income Group (Dataset 2 – Huffington Post)

![Emotion Distribution across Groups](https://raw.githubusercontent.com/Rtf13/Sentiment-analysis-blog/main/assets/images/hp_emotion_distribution_by_income.png)

The same pattern holds for the Huffington Post dataset, suggesting that **sentiment alone does not indicate discriminatory framing** for the groups analyzed.

---

## Content Differences Across Groups

### Word Clouds by Income Group: Dataset 1

<div class="image-grid">
  <div>
    <img src="https://raw.githubusercontent.com/Rtf13/Sentiment-analysis-blog/main/assets/images/high-income-word-cloud-2.png" alt="High Income">
    <p><strong>High Income</strong></p>
  </div>
  <div>
    <img src="https://raw.githubusercontent.com/Rtf13/Sentiment-analysis-blog/main/assets/images/u-middle-word-cloud-2.png" alt="Upper Middle Income">
    <p><strong>Upper Middle Income</strong></p>
  </div>
  <div>
    <img src="https://raw.githubusercontent.com/Rtf13/Sentiment-analysis-blog/main/assets/images/l-middle-word-cloud-2.png" alt="Lower Middle Income">
    <p><strong>Lower Middle Income</strong></p>
  </div>
  <div>
    <img src="https://raw.githubusercontent.com/Rtf13/Sentiment-analysis-blog/main/assets/images/low-income-word-cloud-2.png" alt="Low Income">
    <p><strong>Low Income</strong></p>
  </div>
</div>

---

### Word Clouds by Income Group: Dataset 2

<div class="image-grid">
  <div>
    <img src="https://raw.githubusercontent.com/Rtf13/Sentiment-analysis-blog/main/assets/images/high-income-word-cloud.png" alt="High Income">
    <p><strong>High Income</strong></p>
  </div>
  <div>
    <img src="https://raw.githubusercontent.com/Rtf13/Sentiment-analysis-blog/main/assets/images/u-middle-word-cloud.png" alt="Upper Middle Income">
    <p><strong>Upper Middle Income</strong></p>
  </div>
  <div>
    <img src="https://raw.githubusercontent.com/Rtf13/Sentiment-analysis-blog/main/assets/images/l-middle-word-cloud.png" alt="Lower Middle Income">
    <p><strong>Lower Middle Income</strong></p>
  </div>
  <div>
    <img src="https://raw.githubusercontent.com/Rtf13/Sentiment-analysis-blog/main/assets/images/low-income-word-cloud.png" alt="Low Income">
    <p><strong>Low Income</strong></p>
  </div>
</div>

---

### Interpretation

While sentiment remains largely neutral across all groups, **content differences are substantial**:

- **High-income countries** are associated with diverse topics such as:
  - Climate change
  - Mental health
  - Sports
  - Social media
- **Lower-income countries** are predominantly linked to:
  - War and conflict
  - Crises and coups
  - Violence and death

This does not necessarily imply intentional bias, but it highlights how **repeated exposure to different topic associations can shape public perception**.

---

## Limitations

- Analysis is based on **headlines only**, not full articles
- No ground-truth labels for bias or framing
- Emotion classifier is pretrained and not domain-specific
- Income group is a coarse proxy for vulnerability

---
## Authors

- Leevi Takala  
- Aleena Ahmad  
- Rennze Fabe
