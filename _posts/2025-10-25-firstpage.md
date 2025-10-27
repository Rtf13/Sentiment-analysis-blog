---
title: "Exploring sentiment and content patterns in news articles"
date: 2025-10-25
---

<link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}">

## Overview

News content and the way it is presented can impact public opinions. This is especially important when news discusses groups or communities that are unfamiliar to readers and/or potentially vulnerable.  

This raises the questions: 
*  **are there any noticeable patterns in how news content is written when discussing different groups?**
*  **Does the sentiment, language used, or content differ significantly across groups?**
  
If so, **can we detect and understand these patterns?** Can **we identify the groups that might be vulnerable to harmful patterns?** 

For this purpose, we explored sentiment and content words across various news articles taken from popular sources like **BBC, Huffington Post, Times of India, etc.**  

### Groups Analyzed
First, we wanted to identify potentially vulnerable groups. To derive this from a standardized measure, we used the [World Bank Income Classification Data of 2024](https://datahelpdesk.worldbank.org/knowledgebase/articles/906519-world-bank-country-and-lending-groups), which categorizes countries into four income levels: low, lower middle, upper middle, and high. Here, we would consider countries with lower income levels to be more 'vulnerable' than higher inocme countries.

Our analysis then focuses on the mention of these income groups and entities belonging to these income groups.

### Results:

#### How does sentiment vary across groups? 

Data was analyzed in two datasets, the first (Dataset 1) contained news articles from multiples sources, such as BBC and Times of India. The second (Dataset 2) contained news articles from Huffington Post. From our data, we found the emotions associated with each article and used these to find emotions most commonly associated with each entity and income group. The graphs show the emotion labels across different groups. 

<h3>Emotion distribution by Income Group: Dataset 1 </h3>

![Emotion Distribution across Groups]({{ site.baseurl }}/assets/images/emotion_distribution_by_group.png)

As evident, an overwhelming majority is neutral. Moreoever, no group has a significantly higher proportion of 'negative' or 'positive emotion associated with it, indicating that sentiment is not discriminatory across the groups we chose, for our chosen news sources.

For the Huffington Post dataset, we observe a similar pattern:

<h3>Emotion distribution by Income Group: Dataset 2 </h3>

![Emotion Distribution across Groups]({{ site.baseurl }}/assets/images/hp_emotion_distribution_by_income.png)

#### How does the content vary across groups? 

Besides sentiment, we wanted to see what words and phrases were commonly used in relation with entities. The word clouds below visualize the top 50 words and phrases uniquely associated with each group. 


<h3>Word Clouds by Income Group: Dataset 1 </h3>

<div class="image-grid">
  <div>
    <img src="{{ site.baseurl }}/assets/images/high-income-word-cloud-2.png" alt="High Income">
    <p><strong>High Income</strong></p>
  </div>
  <div>
    <img src="{{ site.baseurl }}/assets/images/u-middle-word-cloud-2.png" alt="Upper Middle Income">
    <p><strong>Upper Middle Income</strong></p>
  </div>
  <div>
    <img src="{{ site.baseurl }}/assets/images/l-middle-word-cloud-2.png" alt="Lower Middle Income">
    <p><strong>Lower Middle Income</strong></p>
  </div>
  <div>
    <img src="{{ site.baseurl }}/assets/images/low-income-word-cloud-2.png" alt="Low Income">
    <p><strong>Low Income</strong></p>
  </div>
</div>



<h3>Word Clouds by Income Group: Dataset 2 </h3>

<div class="image-grid">
  <div>
    <img src="{{ site.baseurl }}/assets/images/hp_high_income_wc_btgram.png" alt="High Income">
    <p><strong>High Income</strong></p>
  </div>
  <div>
    <img src="{{ site.baseurl }}/assets/images/hp_uppermid_income_wc_btgram.png" alt="Upper Middle Income">
    <p><strong>Upper Middle Income</strong></p>
  </div>
  <div>
    <img src="{{ site.baseurl }}/assets/images/hp_lowmid_income_wc_btgram.png" alt="Lower Middle Income">
    <p><strong>Lower Middle Income</strong></p>
  </div>
  <div>
    <img src="{{ site.baseurl }}/assets/images/hp_low_income_wc_btgram.png" alt="Low Income">
    <p><strong>Low Income</strong></p>
  </div>
</div>


Once again, we observe a similar pattern in both datasets. As we move from higher to lower income countries, there is a shift in the content being discussed. 
* The phrases for higher income countries cover a wide range of topics, from climate change, mental health, sports, social media, to some social issues of illness and death.
* For lower income countries, the phrases overwhelmingly concern topics like war, crises, coups, violence, death, etc. In fact, it is difficult to find words that are neutral or positive.

 While this difference in content words alone does not suggest a conscious effort by news media to negatively frame certain groups, it does show that negative topics are more commonly associated with lower income countries. While it can be argued that this stems from these crises and violence being prevalent for lower income countries, it still creates two entirely different images in readers mind regarding these groups. 



