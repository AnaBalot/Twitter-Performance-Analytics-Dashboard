
# 📊 Twitter Data Analytics Dashboard
**Internship Project | Data Cleaning & Dynamic Reporting**

## 📝 Project Overview
In this project, I analyzed a dataset called `tweet.xlsx` to find trends in how people interact with tweets. My main goal was to build a dashboard that is "smart"—meaning it changes what it shows based on the time of day and follows very specific rules for the text and numbers.

## 🛠️ What I Did (Step-by-Step)

### 1. Data Cleaning
I spent a lot of time cleaning the raw Excel file. I had to follow some unique rules for different charts:
* **Text Filtering:** I wrote logic to remove any words that contained specific letters (like 'S', 'H', or 'C') to see how it changed the tweet length and categories.
* **Word Counts:** I filtered the data so some charts only show long tweets (>50 words) and others show short tweets (<30 words).
* **Even & Odd Rules:** I filtered the data to only show results for "Even" dates or "Odd" dates depending on the task.

### 2. Making Charts "Time-Sensitive"
The most interesting part of this project was making the charts disappear and reappear at specific times. I used logic to make sure the dashboard follows these **IST (India Standard Time)** windows:
* **Morning Window (7 AM - 11 AM):** Trends for media and engagement.
* **Afternoon Window (3 PM - 5 PM):** Main performance charts and Top 10 lists.
* **Night Window (6 PM - 11 PM):** Scatter charts for reply analysis.



## 📋 The 6 Main Tasks I Completed

1. **Click Analysis:** A bar chart showing URL and Hashtag clicks for long tweets on Even dates.
2. **Top 10 Performance:** Finding the best tweets by Retweets and Likes, excluding weekends.
3. **Engagement Scatter:** Analyzing tweets with more than 10 replies during night hours.
4. **Summer 2020 Review:** Comparing Likes and Retweets for tweets posted between June and August.
5. **Media Trends:** A dual-axis chart showing how Media Views and Engagements spiked over the last quarter.
6. **Monthly Trends:** A line chart comparing engagement rates for tweets with media vs. tweets without media.

## 💡 Key Logic Used
Instead of just showing all the data, I used **DAX formulas** to act as a "switch." 

**Example of my Visibility Switch:**
```dax
// This code makes the chart stay hidden unless it is between 3 PM and 5 PM IST
Visibility_Switch = 
VAR CurrentHour = HOUR(NOW() + 5.5/24) 
RETURN IF(CurrentHour >= 15 && CurrentHour < 17, 1, 0) 
```
**Advanced Word Removal:**
```powerquery
Text.Combine(
    List.Select(
        Text.Split(Text.Trim([Tweet Content]), " "), 
        each not Text.Contains(_, "s", Comparer.OrdinalIgnoreCase)
    ), 
    " "
)
```

