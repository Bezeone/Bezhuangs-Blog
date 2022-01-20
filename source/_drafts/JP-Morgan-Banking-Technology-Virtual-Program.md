---
title: JPMorgan Chase Software Engineering Virtual Experience Program
date: 2022-01-10
updated: 2022-01-17
tags: [Python]
password: 990312
categories: 程序人生
---

> Virtual work experience programs replicate work at top companies, and connect students to the companies themselves. Throughout this virtual experience provided by JP Morgan, I'm introduced to JPMorgan Chase frameworks and thus apply technical skills to a hypothetical request from the firm’s trading floor to analyze and visualize data. The following are the notes I took during this virtual experience.

<!--more-->

{% pdf /pdf/.pdf %}

### Interface with a stock price data feed

#### Background Information

- Assist with some development to add a chart to a trader’s dashboard allowing them to better identify under/over-valued stocks.
- The trader would like to be able to monitor two historically correlated stocks and be able to visualize when the correlation between the two weakens (i.e. one stock moves proportionally more than the historical correlation would imply). This could indicate a potential trade strategy to simultaneously buy the relatively underperforming stock and sell the relatively outperforming stock. Assuming the two prices subsequently converge, the trade should be profitable.
- Most data visualization for our traders is built on JPMorgan Chase's Perspective data visualization software, which is now open source.
- Before implementing this request using perspective, first we’ll need to interface with the relevant financial data feed and make the necessary adjustments to facilitate the monitoring of potential trade opportunities.

#### Requirements

- Set up the system by downloading the necessary repository, files, tools and dependencies
- Fix the broken client datafeed script in the repository by making the required adjustments to it
- Generate a patch file of the changes made
- Add unit tests in the test script in the repository


### Use JPMorgan Chase frameworks and tools


### Display data visually for traders

### Open source contribution

