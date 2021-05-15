---
title: Data Science Methodology
date: 2021-04-27
updated: 2021-05-15
tags: []
categories: 人工智能与大数据
---

> Despite the recent increase in computing power and access to data over the last couple of decades, our ability to use the data within the decision making process is either lost or not maximized at all too often, we don't have a solid understanding of the questions being asked and how to apply the data correctly to the problem at hand. This course provided by IBM shares a methodology that can be used within data science, to ensure that the data used in problem solving is relevant and properly manipulated to address the question at hand. The following are the notes I took during this course.

<!--more-->

{% pdf /pdf/Data-Science-Methodology.pdf %}

### Data Science Methodologies

- Methodology: a system of methods used in a particular area of study.
- CRISP-DM: the Cross Industry Process for Data Mining methodology.
  - The CRISP-DM methodology is a process aimed at increasing the use of data mining over a wide variety of business applications and industries. 
  - The intent is to take case specific scenarios and general behaviors to make them domain neutral. 
  - CRISP-DM is comprised of six steps with an entity that has to implement in order to have a reasonable chance of success.
  - Business Understanding、Data Understanding、Data Preparation、Modeling、Evaluation、Deployment
  - CRISP-DM is a highly flexible and cyclical model. Flexibility is required at each step along with communication to keep the project on track. 
  - At any of the six stages, it may be necessary to revisit an earlier stage and make changes. The key point of this process is that it’s cyclical.

### From Problem to Approach

- Business Understanding
  - Establishing a clearly defined question starts with understanding the goal of the person asking the question
  - Seek clarification (where is the goal) -> Support the goal -> Get stakeholder "buy-in" and support
  - Case Study: Apply concepts, Define Goals and objectives, Pilot project kickoff, Identify the business requirements
- Analytic Approach
  - Once a strong understanding of the question is established, the analytic approach can be selected. This means identifying what type of patterns will be needed to address the question most effectively
  - The correct approach depends on business requirements for the model
  - If the question is to determine probabilities of an action, Use a predictive model 
  - If the question is to show relationships, Use a descriptive model
  - if the question requires a yes/no answer, Use a classification model
  - It is only when the problem to be addressed is defined, that the appropriate analytic approach for the problem can be selected in the context of the business requirements
  - Case Study: Decision tree classification (Predictive model)

### From Requirements to Collection

- Data Requirements
  - The Data Requirements stage of the data science methodology involves identifying the necessary data content, formats and sources for initial data collection.
  - Prior to undertaking the data collection and data preparation stages of the methodology, it's vital to define the data requirements for decision-tree classification. This includes identifying the necessary data content, formats and sources for initial data collection
  - Case Study: Select the cohort, Define the data
- Data Collection
  - Once the data ingredients are collected, then in the data collection stage, the data scientist will have a good understanding of what they will be working with
  - Techniques such as descriptive statistics and visualization can be applied to the data set, to assess the content, quality, and initial insights about the data. Gaps in data will be identified and plans to either fill or make substitutions will have to be made
  - When collecting data, it is alright to defer decisions about unavailable data, and attempt to acquire it at a later stage
  - Case Study: Gather available data, Merge data

### From Understanding to Preparation 

- Data Understanding
- Data understanding is iterative
- Data Preparation

### From Modeling to Evaluation

- Modeling
- Evaluation

### From Deployment to Feedback

- Deployment
- The refined model must be redeployed.
- This process should be repeated as often as necessary.
- Feedback