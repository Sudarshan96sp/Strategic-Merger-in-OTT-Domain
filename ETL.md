# ETL Process – Strategic Merger in OTT Domain (Jotstar X LioCinema)

This document outlines the ETL (Extract, Transform, Load) process used for analyzing subscriber behavior, content library, and platform performance of Jotstar and LioCinema OTT platforms in preparation for a strategic merger.

---

## 📥 Extract Phase

**Data Sources Used:**

1. **Subscriber Data (CSV / Excel)**  
   - Platform: Jotstar, LioCinema  
   - Columns: `user_id`, `age_group`, `city_tier`, `subscription_date`, `subscription_plan`, `last_active_date`, `plan_change_date`, `new_subscription_plan`

2. **Content Library Data (CSV / Excel)**  
   - Columns: `content_id`, `title`, `genre`, `language`, `type` (Movie/Series), `platform`, `duration`

---

## 🧹 Transform Phase

All transformations were performed using **Power Query** in Power BI. Key transformations include:

### 🔁 1. Data Merging
- Appended Jotstar and LioCinema subscriber tables into a single dataset.
- Unified content library across both platforms.

### 📌 2. Column Engineering
- Created the following new columns:
  - `User_active\inactive`: Categorized users based on last active date.
  - `Current_Subscription_Plan`: Based on plan change history.
  - `Downgrade_Flag`: Flagged as “Downgraded” or “Not Downgraded”.
  - `Upgraded_Flag`: Flagged as “Upgraded” or “Not Upgraded”.

### 📆 3. Date Transformations
- Converted date fields to proper date format:
  - `subscription_date`, `last_active_date`, `plan_change_date`
- Created new columns:
  - `Subscription_Year`, `Subscription_Month`
  - `Inactivity_Days` = `Today - last_active_date`

### 🧮 4. Calculated Measures (in Power BI)
- Total Subscribers
- Total Watch Time
- Percentage of Inactive Users
- Upgrade/Downgrade Rate
- Active Users by City Tier and Age Group
- Content Hours by Genre, Platform

### 🧹 5. Cleaning
- Removed duplicates and null records
- Standardized text casing for consistency
- Filtered out irrelevant or test data

---

## 📦 Load Phase

- Transformed datasets were loaded into Power BI data model.
- Relationships were created:
  - `user_id` (between Subscriber and Content data where relevant)
  - `platform`, `content_id`

- Dashboards were created to highlight:
  - Subscriber demographics and behavior
  - Content consumption patterns
  - Revenue impact from plan upgrades/downgrades
  - Inactivity trends and engagement strategies

---

## 🔄 Refresh Strategy

If automated:
- Power BI Service can refresh data on schedule if connected to a cloud location or OneDrive.
- In this local project, manual refresh was used via Power BI Desktop.

---

## 📊 Output

Final Power BI dashboards provide:
- Interactive insights on content strategy alignment
- Revenue impact analysis
- Data-driven support for merger decisions

---

> 🔍 For a full walkthrough, refer to the `README.md` or check the embedded dashboard visuals.
