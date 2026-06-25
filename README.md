# From Budget to Blockbuster

## Overview

This project explores how financial investment, audience reception, and production trends relate to movie success. Using metadata from over 45,000 films, the analysis examines relationships between budgets, revenues, genres, countries of origin, and ratings from both TMDB and MovieLens.

The goal was to identify factors associated with commercial and critical success, determine which genres and countries consistently produce highly rated films, and evaluate whether larger production budgets translate to greater box office performance. Since movies can be considered successful in many different ways, this project investigates multiple metrics—including profitability, return on investment, popularity, and audience ratings—to better understand what drives movie success.

---

**Source:** The Movies Dataset from Kaggle

https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset

The analysis primarily used the `movies_metadata.csv` table, which contains information on more than 45,000 movies, including:

* Release dates
* Budgets
* Revenues
* Genres
* Languages
* Production companies
* TMDB ratings
* Popularity scores
* Runtime information

Audience feedback was supplemented using the `ratings_small.csv` MovieLens dataset.

The full `ratings.csv` dataset contains over 26 million ratings and could not be loaded into Excel due to row limitations. As a result, `ratings_small.csv` was used instead. Ratings were aggregated by `movieId` to calculate an average MovieLens rating and total rating count for each movie before joining with the metadata dataset.

After cleaning, validation, and transformation in Power Query, the final analytical dataset contained **45,393 movies**.

---

## Business Questions

* Which genres generate the highest return on investment?
* Do larger budgets consistently lead to higher profits?
* Which countries produce the most highly rated films?
* How strongly do popularity, profitability, and ratings align?
* What characteristics distinguish commercially successful movies from critically successful movies?

---

## Tools & Technologies

* **Excel**

  * Pivot Tables
  * Pivot Charts
  * Dashboard Design
  * Slicers and KPI Cards

* **Power Query**

  * Data extraction
  * Cleaning and transformation
  * Validation checks
  * Dataset integration

---

## Methodology

### Data Acquisition

Imported `movies_metadata.csv` as the primary dataset and `ratings_small.csv` as a secondary dataset.

MovieLens ratings were aggregated by `movieId` to calculate:

* Average MovieLens rating
* Total MovieLens rating count

These aggregated values were then joined with the movie metadata table.

---

### Data Cleaning & Validation

All transformations were performed in Power Query.

Cleaning steps included:

* Removing duplicate records
* Removing blanks and errors
* Trimming whitespace
* Standardizing text capitalization
* Correcting data types
* Excluding television series
* Standardizing genre assignments

Validation checks excluded:

* Malformed IMDB identifiers
* Invalid language codes
* Dates earlier than January 1, 1900
* Implausible runtimes
* Suspicious text values

---

### Feature Engineering

Several analytical metrics were created to support comparisons between movies.

**Weighted Composite Score**

A weighted rating metric combining:

* TMDB average rating
* MovieLens average rating
* Rating volume from each platform

This approach reduces the influence of movies with only a small number of ratings.

**Popularity Percentile**

A percentile ranking based on TMDB popularity scores, allowing movies to be compared relative to all other movies in the dataset.

**Revenue-to-Budget Multiple**

A return-on-investment metric calculated as:

```text
Revenue-to-Budget Multiple = Revenue / Budget
```

This metric measures how many times a movie earned back its production budget.

**Title Quality Flag**

A categorical field used to classify movie titles as:

* Valid
* Review
* Invalid

Pattern matching and text heuristics were used to identify potentially corrupted movie titles.

---

### Exploratory Analysis

Pivot Tables were used to investigate:

* Top-rated movies
* Most popular movies
* Highest revenue-to-budget multiples
* Genre performance
* Production trends by country
* Relationships between budget and profit

---

### Dashboard Development

An interactive Excel dashboard was created featuring:

* KPI cards
* Slicers
* Pivot Charts
* Comparative visualizations

Dashboard components include:

* Top-rated movies
* Most popular movies
* Highest ROI movies
* Top production countries
* Budget versus profit comparisons
* Genre performance summaries

---

## Key Findings

### Movie Production is Highly Concentrated

Film production is heavily concentrated within a small number of countries, with the United States contributing substantially more movies than any other country in the dataset.

### Popularity and Profitability Measure Different Types of Success

None of the ten most popular movies appear among the ten movies with the highest revenue-to-budget multiples.

Popularity largely reflects contemporary audience engagement, while profitability reflects financial performance.

### Older Movies Dominate ROI Rankings

Many of the highest revenue-to-budget multiples belong to older movies.

Possible explanations include:

* Lower historical production costs
* Decades of accumulated box office revenue
* Multiple theatrical re-releases

Because inflation adjustments were not incorporated, older movies likely receive an advantage in ROI comparisons.

### Popularity Scores Favor Recent Films

TMDB popularity scores partially depend on online engagement metrics.

As a result, modern movies frequently rank above critically acclaimed classics despite receiving lower review scores.

---

## Limitations

Several limitations should be considered when interpreting these findings.

* Only a small subset of movies contains budget and revenue information.

* `ratings_small.csv` provides substantially less coverage than the complete MovieLens ratings dataset.

* TMDB popularity scores are generated using a proprietary methodology that is not publicly disclosed.

* Movies were assigned a single genre despite many films belonging to multiple categories.

* Inflation adjustments were not performed, introducing bias when comparing financial performance across decades.

Future improvements could include:

* Migrating the project to Power BI to utilize the complete MovieLens ratings dataset
* Adjusting financial metrics for inflation
* Incorporating ratings from additional review platforms
* Modeling movies with multiple genre assignments instead of a single primary genre