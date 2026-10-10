# Traffic Collision Analysis

A project to analyse California traffic collision data using Apache Spark (PySpark). The analysis explores patterns in collision severity, location-based risk, weather, lighting and road conditions, and time-based trends, to support data-driven road safety decisions.

## Dataset

Data comes from the Statewide Integrated Traffic Records System (SWITRS) and is provided in `Crash_Data_Analysis_Dataset.zip`. After extraction, the notebook reads `sample_*.csv` files from the `Crash_Data_Analysis_Dataset/` folder:

| Table | Description |
|-------|-------------|
| `collisions` | Collision details: location, time, conditions, vehicles involved, victim counts |
| `parties` | Parties involved: age, sex, sobriety, vehicle info |
| `victims` | Injuries of individual people involved |
| `case_ids` | Case identifiers and database year |

## Repository Contents

| File | Description |
|------|-------------|
| `ETL_Traffic_Data_Analysis.ipynb` | Main notebook: data prep, cleaning, EDA and ETL queries |
| `Crash_Data_Analysis_Dataset.zip` | Source dataset |
| `Report.pdf` / `Report.odt` | Written report of findings and recommendations |

## Analysis Workflow

1. **Data Preparation** – load CSVs into Spark DataFrames and inspect schemas.
2. **Data Cleaning**
   - Missing values: categorical fields filled with `Unknown`, victim counts with `0`.
   - Type fixes: date columns converted with `to_date`.
   - Duplicates removed where found.
   - Outliers: detected with the IQR method; implausible values removed (e.g. `distance > 10000`, `victim_age` of 999 or outside 0–120).
3. **Exploratory Data Analysis** – severity distribution, weather and lighting impact, victim age, weekday/monthly/hourly trends, county-level and geographic distribution.
4. **ETL Querying (PySpark SQL)** – top counties, peak month, common weather, fatality percentage, most dangerous time of day, road surface and lighting conditions.
5. **Conclusion** – insights and recommendations for road safety and traffic management.

## Tech Stack

- Python, Jupyter Notebook
- Apache Spark (PySpark 3.5.4)
- pandas, matplotlib, seaborn

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/pankajy-dev/traffic-collision-analysis.git
   cd traffic-collision-analysis
   ```
2. Install dependencies:
   ```bash
   pip install pyspark==3.5.4 pandas==2.2.2 matplotlib seaborn jupyter
   ```
3. Extract the dataset in the repository root:
   ```bash
   unzip Crash_Data_Analysis_Dataset.zip
   ```
4. Open and run `ETL_Traffic_Data_Analysis.ipynb`:
   ```bash
   jupyter notebook ETL_Traffic_Data_Analysis.ipynb
   ```

## Report

See [`Report.pdf`](Report.pdf) for the full findings, visualisations and recommendations.
