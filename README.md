# COVID-19 Data Analysis & Visualization

This project provides an in-depth analysis of global COVID-19 data using clustering techniques and various visualizations. The goal is to identify trends in confirmed cases, mortality rates, incident rates, and recent case statistics.

## Libraries Used

* **Pandas**: Data manipulation and cleaning
* **Matplotlib**: Creating static visualizations
* **Seaborn**: Enhancing visualizations with statistical plots
* **GeoPandas**: Geospatial data handling and mapping
* **NumPy**: Numerical operations
* **Scikit-Learn**: Machine learning tools (K-Means Clustering, StandardScaler)

## Installation

To install required packages:

```bash
pip install pandas matplotlib seaborn geopandas numpy scikit-learn
```

## Data Source

The dataset includes the following fields:

* Country/Region
* Last Update
* Latitude/Longitude
* Confirmed cases
* Deaths
* Incident Rate
* Mortality Rate
* Cases and Deaths in the last 28 days

## Project Workflow

### 1. Data Preprocessing

* Loading the dataset using Pandas
* Handling missing values
* Creating additional features like 28-day percentage change

### 2. K-Means Clustering

Clustering countries based on Incident Rate and Mortality Rate to detect similar behavior:

```python
features = cd[["Incident_Rate", "Mortality_Rate"]].fillna(0)
scaler = StandardScaler()
scaled = scaler.fit_transform(features)
kmeans = KMeans(n_clusters=3, random_state=42)
cd["Cluster"] = kmeans.fit_predict(scaled)
```

### 3. Visualizations

* **Scatter Plot (Bubble Chart)**: Confirmed vs Deaths with bubble size by Incident Rate
* **Cluster Plot**: Displaying country groupings from K-Means
* **Highlighting Special Cases**:

  * Low Confirmed, High Mortality (possible underreporting)
  * Rapid case decline (low Cases\_28\_Days %)
  * High Cases\_28\_Days with zero Deaths (strong healthcare response)

### 4. Geospatial Mapping

* Using GeoPandas and shapefiles to plot:

  * Heatmap of confirmed cases by coordinates
  * Choropleth maps for Mortality Rate and 28-day stats (optional)

## How to Run

1. Ensure all dependencies are installed.
2. Place the dataset in the project directory.
3. Open and run the `Analysis.ipynb` notebook or execute the script.

## File Structure

```
COVID-19-Data-Analysis/
├── Analysis.ipynb                # Main Jupyter Notebook
├── analysis.py                   # Python script version
├── cases_country.csv             # COVID-19 dataset
├── ne_110m_admin_0_countries.shp # Country shapefile for mapping
├── README.md                     # This file
```

## Future Enhancements

* Advanced clustering (DBSCAN, Hierarchical)
* Time-series forecasting for individual countries
* Interactive maps using Plotly/Folium

---

**Author**: Riyocodeart
**Date**: June 2025
