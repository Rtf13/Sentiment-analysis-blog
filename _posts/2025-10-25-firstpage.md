---
title: "Exploring-Sentiment-Patterns-In-News-Articles"
date: 2025-10-25
---
## Overview

Do patterns of news content vary for different groups? Does the sentiment and language used differ significantly across different groups? If so, how can we detect and understand these patterns? How can we identify the groups that might be vulnerable to negative reporting? 

We explored sentiment and content word patterns across different news articles to see if any significant differences exist. 

### Groups Analyzed
In particular, for our analysis, we wanted to identify potentially vulnerable and less vulnerable groups. For this purpose, our analysis is based on [World Bank Income Classification Data of 2024] (https://datahelpdesk.worldbank.org/knowledgebase/articles/906519-world-bank-country-and-lending-groups), which categorizes countries into four income levels: low, lower middle, upper middle, and high. 

With our results, you can see how sentiment and content words used in news articles vary for these groups. 

### Datasets

We used 4 news datasets in our analysis, for a total of over 1000000 articles analysed

### Method 

We applied the `michellejieli/emotion_text_classifier` model from HuggingFace to classify emotions

### Results:

#### How does sentiment vary across groups? 

The graphs show the emotion labels across different groups. As evident, an overwhelming majority is neutral. Moreoever, no group has a significantly higher proportion of 'negative' or 'positive emotion associated with it, indicating that sentiment is not discriminatory across the groups we chose. 

However, a deeper analysis at entity level shows that some entities have an overall negative score associated with them. 

#### How does the content vary across groups? 

We visualized the words and phrases uniquely associated with each group. 

![High Income Countries: Top Words](/assets/images/high-income-word-cloud.png)
![Upper Middle Income Countries: Top Words](/assets/images/u-middle-word-cloud.png)
![Lower Middle Income Countries: Top Words](/assets/images/l-middle-word-cloud.png)
![Low Income Countries: Top Words](/assets/images/low-income-word-cloud.png)

As you can see, there is a clear difference in the content that is discussed for higher income countries and lower income countries. 
