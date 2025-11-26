# RecipeDB3_PatternMining

# Recipe Pattern Mining & Ingredient Association Analysis

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![Library](https://img.shields.io/badge/Library-mlxtend%20|%20NetworkX-green)

This project performs **Association Rule Mining** and **Network Analysis** on a large culinary dataset (RecipeDB) to uncover hidden relationships between ingredients. By utilizing the **Apriori algorithm**, the project identifies frequent ingredient pairings, analyzes recipe complexity, and visualizes the culinary network of specific dishes like "Chicken" and "Biryani."

## Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [Dataset](#dataset)
- [Installation & Requirements](#installation--requirements)
- [Methodology](#methodology)
- [Key Insights](#key-insights)
- [Visualizations](#visualizations)

## Overview
Understanding how ingredients combine is fundamental to culinary science. This project takes a data-driven approach to:
1.  **Analyze** the frequency of ingredients across thousands of recipes.
2.  **Discover** which ingredients are statistically most likely to appear together.
3.  **Visualize** these relationships as a network graph to understand the "backbone" of certain cuisines.

## Key Features
* **Data Preprocessing:** Transformation of raw ingredient lists into transaction-based formats suitable for mining.
* **Exploratory Data Analysis (EDA):** Statistical breakdown of the most common ingredients and recipe sizes.
* **Pattern Mining:** Application of the **Apriori Algorithm** to find Frequent Itemsets.
* **Association Rules:** Calculation of Support, Confidence, and Lift to determine the strength of ingredient relationships.
* **Network Graphing:** Visualization of ingredient co-occurrences using **NetworkX**.
* **Semantic Querying:** Filtering based on specific food categories (e.g., Spices, Chicken).

## Dataset
The notebook relies on data from **RecipeDB**. Ensure the following files are present in your root directory:
* `RecipeDB_ingredient_phrase.csv`: Contains raw ingredient data mapped to recipe IDs.
* `RecipeDB_ingredient_flavor.csv`: Contains metadata regarding ingredient categories and flavors.

> **Note:** The script generates an intermediate file named `transformed_recipes.csv` during execution.

## 🛠 Installation & Requirements
To run this notebook, you will need Python installed along with the following libraries:

```bash
pip install pandas numpy matplotlib networkx mlxtend
````

### Running the Project

1.  Clone this repository.
2.  Place the source CSV files in the project folder.
3.  Launch Jupyter Notebook:
    ```bash
    jupyter notebook recipedb3_patternMining.ipynb
    ```
4.  Run all cells to execute the analysis pipeline.

## Methodology

The analysis follows these steps:

1.  **Ingestion:** Loading raw CSV data and extracting relevant columns (`recipe_no`, `ingredient`).
2.  **Grouping:** Aggregating ingredients into lists per recipe ID to create a "basket" format.
3.  **Global Stats:** Calculating unique ingredient counts (20,280 identified) and top ingredients.
4.  **Case Study - "Chicken":**
      * Filtering recipes containing "Chicken".
      * Calculating co-occurrence matrices.
      * Building a directed graph of the top 100 associations.
5.  **Case Study - "Biryani":**
      * Specific analysis of 91 Biryani recipes.
      * Identifying complex itemsets (e.g., groupings of 4 specific spices).

## Key Insights

  * **Most Common Ingredients:** Across the entire dataset, the staples are Salt, Onion, Butter, and Garlic.
  * **Recipe Complexity:** Recipes range drastically in size, from 2 ingredients (minimalist) to 38 ingredients (complex).
  * **Biryani Composition:** The analysis identified that `Basmati Rice`, `Cinnamon`, `Bay Leaf`, and `Clove` form a highly frequent itemset (appearing together in \~37% of Biryani recipes).
  * **Strong Rules:** High-confidence rules were found, such as `{Allspice} -> {Chicken}`.

## Visualization Using Cytoscape

A key component of our project is **network visualization using Cytoscape**.

We imported our ingredient network into Cytoscape to generate multiple visual representations:

### 1. Ingredient Co-Occurrence Graph
- Nodes sized by ingredient frequency  
- Edges weighted based on co-occurrence strength (how often two ingredients appear together)

### 2. Communities / Clusters
- Groups of ingredients forming cuisine-specific clusters  
- Examples:  
  - *Indian masala cluster*  
  - *Italian herb cluster*

### 3. High-Degree Ingredient Hubs
- Central, widely occurring ingredients such as:  
  - Garlic  
  - Onion  
  - Tomato  
  - Oil
    
These ingredients often appear as major hubs in the network.

-----


```
```
