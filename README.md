# Meta Performance Dashboard — Facebook & Instagram Ads Analysis

## 📌 Project Overview

This project analyzes advertising performance data using **Microsoft Power BI** to uncover meaningful insights about ad campaign performance across **Facebook** and **Instagram**.

The project follows an end-to-end analytics workflow:

**Ad Campaign Data → Data Modeling → DAX Measures → Power BI Dashboard → Business Insights**

The dataset covers **400,000 ad events** across **200 ads** and **50 campaigns**, running from **May 7, 2025 to August 6, 2025**, and includes:

- Overall campaign reach and engagement performance
- Facebook vs Instagram platform performance
- Click-through and conversion effectiveness
- Audience behavior by age, gender, country, and interests
- Ad type performance
- Budget utilization and efficiency
- Weekly and hourly engagement trends

---

## 🎯 Project Objectives

The main objectives of this project are:

1. Model ad event, ad, campaign, and user data into a clean semantic model.
2. Build DAX measures for reach, engagement, and conversion metrics.
3. Analyze performance separately for Facebook and Instagram.
4. Identify which ad types and audiences drive the strongest engagement.
5. Track click-through rate (CTR), conversion rate, and purchase rate.
6. Analyze engagement trends by week/day and by time of day.
7. Monitor total and average campaign budget, and cost efficiency.
8. Break down performance by audience demographics (age, gender, country, interests).
9. Build an interactive Power BI dashboard for marketing decision-making.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Power BI | Dashboard, data modeling, and visualization |
| DAX | Measures and calculated metrics |
| Power Query | Data shaping and transformation |
| GitHub | Project documentation and version control |

---

## 📂 Project Structure

```text
Meta-Performance-Dashboard/
│
├── dataset/
│   ├── campaigns.csv
│   ├── users.csv
│   ├── ads.csv
│   └── ad_events.csv
│
├── PowerBI/
│   └── META_PERFORMANCE_DASHBOARD.pbix
│
├── Dashboard_images/
│   ├── facebook_overview.png
│   ├── instagram_overview.png
│
└── README.md
```

---

## 📂 Dataset

### Dataset Overview

The project uses a **Meta Ads dataset** made up of four related tables: ad-level events, ad attributes, campaign metadata, and audience/user attributes.

| Table | Rows | Description |
|---|---|---|
| `ad_events.csv` | 400,000 | Fact table — one row per impression/click/like/comment/share/purchase event |
| `ads.csv` | 200 | Ad-level attributes (platform, type, targeting) |
| `campaigns.csv` | 50 | Campaign metadata and budget |
| `users.csv` | 9,841 | Audience attributes (age, gender, country, interests) |

### 📊 Dataset Columns

**`ad_events.csv`**: `event_id`, `ad_id`, `user_id`, `timestamp`, `day_of_week`, `time_of_day`, `event_type` (Impression, Click, Like, Comment, Share, Purchase)

**`ads.csv`**: `ad_id`, `campaign_id`, `ad_platform` (Facebook/Instagram), `ad_type` (Image, Video, Carousel, Stories), `target_gender`, `target_age_group`, `target_interests`

**`campaigns.csv`**: `campaign_id`, `name`, `start_date`, `end_date`, `duration_days`, `total_budget`

**`users.csv`**: `user_id`, `user_gender`, `user_age`, `age_group`, `country`, `location`, `interests`

### 📈 Derived Metrics (DAX Measures)

| Metric | Formula |
|---|---|
| Impressions | `COUNT` of `event_type = "Impression"` |
| Clicks | `COUNT` of `event_type = "Click"` |
| CTR | `Clicks / Impressions` |
| Engagements | Clicks + Likes + Comments + Shares |
| Engagement Rate | `Engagements / Impressions` |
| Purchases | `COUNT` of `event_type = "Purchase"` |
| Conversion Rate | `Purchases / Clicks` |
| Purchase Rate | `Purchases / Impressions` |
| Total Budget | `SUM(campaigns.total_budget)` |
| Avg Budget per Campaign | `Total Budget / Distinct Campaigns` |
| Cost per Click | `Total Budget / Clicks` |
| Cost per Purchase | `Total Budget / Purchases` |

---

## 💡 Business Insights Discovered

### 📈 1. Reach & Engagement — Overall

| Metric | Value |
|---|---|
| Total Impressions | **339,812** |
| Total Clicks | **40,079** |
| CTR | **11.79%** |
| Total Engagements (Clicks + Likes + Comments + Shares) | **58,157** |
| Engagement Rate | **17.11%** |
| Total Purchases | **2,031** |
| Conversion Rate (Purchases / Clicks) | **5.07%** |
| Purchase Rate (Purchases / Impressions) | **0.60%** |

Of total engagements, **Clicks (40,079)** make up the majority by far, followed by **Likes (12,013)**, **Comments (4,108)**, and **Shares (1,957)**.

### 📊 2. Platform Comparison — Facebook vs Instagram

| Metric | Facebook | Instagram |
|---|---|---|
| Ads running | 127 | 73 |
| Impressions | **215,972** | 123,840 |
| Clicks | 25,389 | 14,690 |
| CTR | 11.76% | **11.86%** |
| Engagements (Clicks+Likes+Comments+Shares) | **36,801** | 21,356 |
| Engagement Rate | 17.04% | **17.24%** |
| Purchases | **1,323** | 708 |
| Conversion Rate | **5.21%** | 4.82% |

**Facebook** carries roughly **1.7x** the volume of Instagram (proportional to its larger ad count) and drives more total purchases, but **Instagram edges out slightly higher CTR and engagement rate** per impression. Facebook converts clicks to purchases more efficiently overall (5.21% vs 4.82%).

### 🛍️ 3. Ad Type Performance

| Ad Type | Impressions | CTR | Engagement Rate | Conversion Rate |
|---|---|---|---|---|
| **Stories** | **108,932** | 11.73% | 17.10% | **5.34%** |
| Image | 88,164 | 11.88% | 17.18% | 4.67% |
| Carousel | 86,673 | 11.72% | 17.00% | 5.13% |
| Video | 56,043 | **11.90%** | **17.22%** | 5.07% |

**Stories** is the strongest all-round format — highest volume and highest conversion rate. **Video** has the smallest reach but the best CTR and engagement rate, suggesting it's efficient at driving interaction where it does run. **Image** has the weakest conversion rate despite solid reach and CTR — a candidate for creative/offer review.

### 👥 4. Audience Insights

**Top countries by impressions:** United States (97,336), United Kingdom (48,965), Canada (32,139), India (30,268), Germany (26,980).

The **US** leads on both volume and conversion rate (5.49%). Smaller markets stand out on efficiency — **Japan** converts best overall at **6.25%** despite modest volume (15,945 impressions), and **Mexico** follows at 5.94%. **France** has the weakest conversion rate among the top 10 (3.91%).

**Age groups:** 25–34 is the largest segment (133,113 impressions), followed by 18–24 (101,138). The 55–65 group is smallest by far (2,610) but has a strong conversion rate (5.72%) relative to its size.

**Gender:** Male users generate the most volume (179,326 impressions), but Female users have the slightly higher CTR (11.91% vs 11.72%) and comparable conversion rate.

**Interests:** Fairly evenly distributed — fitness, technology, art, travel, and gaming are the top-tracked interest tags, each appearing in ~50,000 impressions, with no single interest dominating.

### 💰 5. Budget & Efficiency

| Metric | Value |
|---|---|
| Total Budget (50 campaigns) | **$2,535,923.78** |
| Average Budget per Campaign | **$50,718.48** |
| Cost per Click | **$63.27** |
| Cost per Purchase | **$1,248.61** |

36 of 48 active campaigns run ads on **both** Facebook and Instagram simultaneously, so budget is generally shared across platforms rather than allocated to just one.

### 🕒 6. Time-Based Patterns

Volume and rates are fairly stable across the week and day — this dataset doesn't show a dramatic single "peak" period, but a few small edges stand out:

- **Best CTR by time of day:** Afternoon (11.91%)
- **Best engagement rate by time of day:** Evening (17.18%)
- **Best CTR by day of week:** Friday (11.95%)/Tuesday (11.90%)
- **Best engagement rate by day of week:** Monday/Tuesday (17.20%)

### 🏆 7. Top & Bottom Campaigns (by impressions)

| Rank | Campaign | Impressions |
|---|---|---|
| 🥇 Top | Campaign_42_Summer | 13,671 |
| 🥈 | Campaign_24_Summer | 13,638 |
| 🥉 | Campaign_20_Winter | 13,607 |
| Bottom | Campaign_35_Launch | 1,686 |

---

## 📊 Key Performance Indicators

The Power BI dashboard provides the following major KPIs on both the Facebook and Instagram pages:

| KPI | Overall Value |
|---|---|
| **Impressions** | 339,812 |
| **Clicks** | 40,079 |
| **CTR** | 11.79% |
| **Engagements** (Clicks+Likes+Comments+Shares) | 58,157 |
| **Engagement Rate** | 17.11% |
| **Purchases** | 2,031 |
| **Conversion Rate** | 5.07% |
| **Purchase Rate** | 0.60% |
| **Total Budget** | $2,535,923.78 |
| **Avg Budget per Campaign** | $50,718.48 |
| **Cost per Click** | $63.27 |
| **Cost per Purchase** | $1,248.61 |

---

## 🎯 Key Business Takeaways

1. **Stories** is the best-performing ad type overall — prioritize it for reach and conversions.
2. **Instagram** slightly outperforms Facebook on CTR and engagement rate per impression, even though Facebook drives more total volume and purchases — worth testing higher Instagram budget share.
3. **Video** has the best CTR but the smallest footprint — an opportunity to scale up if conversion holds at higher volume.
4. **Image** ads convert the worst relative to their reach — review creative or offer.
5. The **US, UK, and Canada** drive the most volume, but **Japan and Mexico** convert best per impression — worth testing budget reallocation toward high-efficiency markets.
6. The **25–34** age group is the primary audience by volume; the **55–65** segment is small but efficient.
7. Engagement and CTR are stable throughout the week — no major day/time is underperforming, so scheduling isn't a strong lever here.
8. With 36 of 48 campaigns spanning both platforms, budget and creative strategy should generally be planned cross-platform rather than platform-by-platform.

---

## 🔎 Summary

The analysis demonstrates that **reach alone is not sufficient to evaluate ad performance**. Facebook has the larger footprint, but Instagram is the more efficient platform per impression. Stories format leads across nearly every metric, while Image ads underperform on conversion despite solid reach. Combining **Impressions + Clicks + CTR + Engagement Rate + Conversion Rate + Purchases + Budget** gives a much more complete view of what's actually working.

---

## 📈 Project Outcome

The project transforms raw Meta ad event data into an interactive business intelligence solution, providing a consolidated view of **Reach + Engagement + Conversion + Audience + Budget** across Facebook and Instagram, with filters and slicers for interactive analysis.

---

## 👨‍💻 Author

**KARTIKEYA BHATNAGAR**

**Technologies:** Power BI · DAX · Power Query · Data Analytics

---

## ⭐ If you found this project useful

If you find this project useful or interesting, consider giving the repository a ⭐ on GitHub.

### A few things to add to your actual GitHub repository

Once you've taken screenshots of your actual Facebook and Instagram dashboard pages, add them under `Dashboard_images/` and reference them here — that will make the project immediately understandable to recruiters visiting your GitHub.
