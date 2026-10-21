# Amazon Prime Content Analytics & Insights

Exploratory Data Analysis and Visualization of the Amazon Prime Movies and TV Shows Dataset

Student: Taksh Chavda | Enrollment No.: IU2441230680
Team Mate(s): IU2441230663
Indus University (IITE) - B.Tech CSE | Faculty: Vatsal Shinghala

---

## 1. Project Definition

This project cleans and analyses the Amazon Prime titles dataset to understand how the
catalogue is composed, how it has grown over time, which countries and genres
dominate, and which audience the content targets.

Objectives:

- Clean the data (missing values, duplicates, data types, outliers)
- Compare Movies vs TV Shows
- Analyse catalogue growth by year added and release year
- Identify top countries, genres and ratings
- Study movie duration and number of TV seasons
- Present findings through clear visualizations and a short insights report

---

## 2. Dataset Use Case

| Attribute         | Details                                                                 |
| ----------------- | ----------------------------------------------------------------------- |
| File              | amazon_prime_titles.csv                                                 |
| Records / Columns | 9,668 rows x 12 columns (raw data)                                      |
| Source            | [Amazon Prime Movies and TV Shows (Kaggle)](https://www.kaggle.com/datasets/shivamb/amazon-prime-movies-and-tv-shows) |

Columns: show_id, type, title, director, cast, country, date_added,
release_year, rating, duration, listed_in, description

Use cases: content strategy, market analysis, audience targeting,
trend analysis, and a future content-based recommendation system.

### Data Cleaning Summary

| Step           | What the notebook does                                                        |
| -------------- | ----------------------------------------------------------------------------- |
| Text cleanup   | Strips whitespace and turns empty strings into missing values                 |
| Missing values | Prints a missing-value table; fills director, cast, country, rating with "Unknown". Rows without date_added are kept and only excluded from date charts |
| Bad entries    | Detects durations typed in the rating column and moves them to duration       |
| Duplicates     | Checks duplicate rows and duplicate show_id values, removes them              |
| Data types     | date_added -> datetime; duration split into duration_min (movies) and seasons (TV shows) |
| Outliers (IQR) | Flags long/short movies and long-running shows; kept because they are real values |

The cleaned dataset is saved as `data/amazon_prime_cleaned.csv`.
Exact counts for every step are printed in the notebook and written to `docs/results_summary.md`.

---

## 3. Visualizations and Outcomes

| No. | Visualization                         | What it shows                                  | Outcome                                          |
| --- | ------------------------------------- | ---------------------------------------------- | ------------------------------------------------ |
| 1   | Pie chart - Movies vs TV Shows        | Content split                                  | 80.8% Movies / 19.2% TV Shows                    |
| 2   | Stacked bar - Titles added per year   | Catalogue growth by year added                 | Peak year: 2021                                  |
| 3   | Bar chart - Top 10 countries          | Main content-producing countries               | Top 3: United States, India, United Kingdom      |
| 4   | Bar chart - Top 10 genres             | Dominant genres                                | Top 3: Drama, Comedy, Action                     |
| 5   | Bar chart - Rating distribution       | Target audience                                | Top ratings: 13+, 16+ (39.3% of rated titles)    |
| 6   | Histogram - Movie duration            | Typical movie length                           | Median: 91 minutes                               |
| 7   | Bar chart - TV seasons                | How long shows run                             | 72.4% have 1 season                              |
| 8   | Heatmap - Year vs Month added         | Busiest months for new additions               | See heatmap in `images/` (subset with date_added) |
| 9   | Line chart - Titles by release year   | How recent the catalogue is                    | 56.0% released 2015 or later                     |

The notebook saves every chart to the `images/` folder. Full numbers are in `docs/results_summary.md`.

---

## 4. Key Insights

- The catalogue is Movie-heavy: 9,668 titles, of which 80.8% are Movies and 19.2% are TV Shows.
- Most titles were added in 2021 (among titles that have a date_added).
- The top content producers are the United States, India and the United Kingdom.
- Drama, Comedy and Action are the most common genres.
- The content mainly targets teen and young-adult viewers: the two most common ratings are 13+ and 16+, covering 39.3% of rated titles.
- Median movie length is 91 minutes, and 72.4% of TV shows have only 1 season.
- The catalogue is fairly recent: 56.0% of titles were released in 2015 or later.

Data note: in this dataset, `date_added` is known for only 1.6% of titles and `country` for 7.0%.
The date-based and country charts therefore describe only that subset of the catalogue.

---

## 5. Python Libraries and Tools

| Library / Tool         | Purpose                                       |
| ---------------------- | --------------------------------------------- |
| Python 3.x             | Core language                                 |
| Pandas, NumPy          | Data loading, cleaning and numeric operations |
| Matplotlib, Seaborn    | Static visualizations and heatmaps            |
| Google Colab / Jupyter | Running and presenting the notebook           |
| Git & GitHub           | Version control and team collaboration        |

Install:

```
pip install -r requirements.txt
```

---

## 6. Repository Structure

```
amazon-prime-content-analysis1/
|-- data/
|   |-- amazon_prime_titles.csv      (download from Kaggle, see data/README.md)
|   |-- amazon_prime_cleaned.csv     (created by the notebook)
|-- notebooks/
|   |-- Amazon_Prime_Cleaning_Visualization.ipynb
|-- images/
|   |-- (charts exported by the notebook)
|-- docs/
|   |-- results_summary.md           (created by the notebook)
|-- requirements.txt
|-- .gitignore
|-- README.md
```

---

## 7. How to Run

1. Clone the repository:
   ```
   git clone https://github.com/harshthakkar230806-cmyk/amazon-prime-content-analysis1.git
   cd amazon-prime-content-analysis1
   ```
2. Download `amazon_prime_titles.csv` from Kaggle and place it in the `data/` folder
   (details in `data/README.md`).
3. Open `notebooks/Amazon_Prime_Cleaning_Visualization.ipynb` in Jupyter or Google Colab.
   On Colab, run the first cells and upload the CSV when asked.
4. Run all cells in order (Runtime > Run all).

---

## 8. Team Contribution

| Task                     | Member 1 (Harsh) | Member 2 |
| ------------------------ | ---------------- | -------- |
| Data cleaning            | Yes              | Review   |
| Visualizations 1-4       | Yes              | -        |
| Visualizations 5-9       | -                | Yes      |
| README and documentation | Yes              | Yes      |

---

## 9. Conclusion

The project turns the raw Amazon Prime catalogue into clear visual insights about its mix of
movies and TV shows, where the content comes from, which genres and ratings dominate, and how
the catalogue grew. The catalogue is dominated by Movies (80.8%), led by Drama, Comedy and Action,
and aimed mostly at teen and young-adult audiences. Future scope: build a content-based
recommendation system using genre, cast and description, and compare the Amazon Prime catalogue
with Netflix.