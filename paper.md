---
title: 'RoBVis: An Interactive Shiny Application for Visualizing Risk of Bias Assessments' # Or choose your own title
tags:
  - R
  - Shiny
  - risk of bias
  - systematic review
  - data visualization
  - ROB2
  - ROBINS-I
  - QUADAS-2
authors:
  - name: [Mahmood ahmad], [Parichatra Homhuan], [Najia ahmad], [Abdullahi Noori], [Kaleem Asad], [Hyuk Woo]      


affiliations:
 - name: [Royal Free Hospital ]
  
date: [Date of submission, e.g., 23 April 2025]
bibliography: paper.bib # Assumes your bibliography file is paper.bib

# Summary

Assessing and reporting the risk of bias (RoB) in primary studies is a fundamental step in conducting high-quality systematic reviews. Effective visualization of these assessments aids transparency and helps readers understand the quality of the synthesized evidence. RoBVis is an interactive web application developed using R [@R-base] and Shiny [@shiny] designed to streamline the generation of commonly used RoB summary graphics. It specifically supports data derived from several widely adopted assessment tools: ROB2 [@ROB2], ROBINS-I [@ROBINS_I], QUADAS-2 [@QUADAS_2], ROB1, and the Newcastle-Ottawa Scale (NOS). Users can upload their assessment data via CSV or Excel files, or use built-in sample datasets. RoBVis then generates interactive summary bar charts (`plotly` [@plotly]), per-study traffic light plots (`ggplot2` [@ggplot2]), and domain-specific frequency distribution plots (`ggplot2`). It also includes an option for exploratory k-means clustering (`factoextra` [@factoextra]) to identify potential patterns in study assessments. RoBVis aims to provide a user-friendly, code-free environment for researchers to rapidly visualize, explore, and export standard RoB graphics.

# Statement of Need

While various R packages like `robvis` exist for creating RoB plots programmatically, generating these visualizations often requires coding knowledge and iterative refinement in R. Furthermore, researchers might need to use different functions or scripts to produce the standard summary bar chart versus the traffic light plot. RoBVis addresses these challenges by providing an integrated, interactive Shiny application where users can achieve these common visualization tasks through a graphical interface. Key motivations include:

1.  **Accessibility:** Lowering the technical barrier for researchers who may not be proficient R programmers but still need to produce standard RoB plots.
2.  **Efficiency:** Allowing rapid generation and exploration of different plot types from the same uploaded dataset without rewriting code.
3.  **Multi-Tool Support:** Handling the specific domains and judgment levels of several common RoB tools (ROB2, ROBINS-I, QUADAS-2, ROB1, NOS) within a single application.
4.  **Integrated Workflow:** Combining data upload, tool selection, plot generation, basic analysis (clustering), and export features in one place.
5.  **Learning Aid:** Providing sample datasets for each tool helps users understand the required input format.

RoBVis is targeted at systematic reviewers, meta-analysts, guideline developers, health technology assessment professionals, and students involved in evidence synthesis who need to visualize RoB assessments efficiently.

# Key Functionality

RoBVis offers the following core features, accessible through a `bs4Dash` [@bs4Dash] sidebar menu:

* **Data Handling:**
    * Accepts user data uploaded as CSV (via `readr` [@readr]) or Excel (`readxl` [@readxl]) files.
    * Expects a 'Study' identifier column and columns named according to the domains of the chosen RoB tool (e.g., 'Randomization', 'Deviations' for ROB2). An optional 'Overall' judgment column can also be used.
    * Includes sample datasets for ROB2, ROBINS-I, QUADAS-2, ROB1, and NOS that can be loaded directly.
    * Displays the loaded data in an interactive table using `DT` [@DT].
* **RoB Tool Selection:** A dropdown menu allows users to specify which RoB tool was used for the assessment, ensuring correct domain mapping and color palettes.
* **Summary Plot:**
    * Generates a stacked bar chart showing the percentage of studies rated at each judgment level (e.g., Low, Some concerns, High) for each domain.
    * Uses `ggplot2` for plotting logic and `plotly` for interactive rendering (hover-over details).
    * Optionally includes the 'Overall' judgment column in the plot.
    * Allows selection between different `ggplot2` themes.
* **Traffic Light Plot:**
    * Creates a grid visualizing the judgment for each individual study across all relevant RoB domains (plus 'Overall', if present).
    * Uses distinct colors (typically green/yellow/red or similar, adapted per tool) for different judgment levels.
    * Generated using `ggplot2`. Point size is adjustable via a slider.
* **Frequency Distribution Plot:**
    * Displays faceted bar charts, where each facet represents an RoB domain.
    * Bars show the raw count of studies receiving each judgment level within that specific domain.
    * Generated using `ggplot2`.
* **Cluster Analysis (Exploratory):**
    * Converts categorical RoB judgments to numeric scores based on the selected tool.
    * Performs k-means clustering on the studies using these scores via `factoextra`.
    * Visualizes the clusters using the first two principal components, helping to identify groups of studies with similar RoB profiles. The number of clusters (k) can be selected by the user.
* **Exporting:**
    * Allows downloading of the summary, traffic light, and frequency plots as PNG files.
    * Allows downloading of generated summary, traffic light (long format), and frequency tables as CSV files using base R functions and `writexl` [@writexl] for Excel format where applicable.
    * Provides a simple text report download summarizing key data points.

# Example Usage

Using RoBVis typically follows these steps:

1.  **Load Data:** Navigate to the 'Data Management' tab. Either use the 'Pick a Sample Dataset' radio buttons and click 'Load Selected Sample', or use the 'Upload a File' control to load your own CSV/Excel file.
2.  **Select Tool:** Ensure the 'Risk of Bias Tool' dropdown correctly reflects the tool used for the loaded data (e.g., select "ROB2").
3.  **View Data:** Check the loaded data in the 'Data Table' on the right.
4.  **Explore Plots:** Click on 'Summary Plot', 'Traffic Light', or 'Frequency' in the sidebar to view the corresponding visualizations. Use options within the collapsible cards on each tab (e.g., check 'Include Overall Column?', adjust 'Point Size') to customize the plots.
5.  **Analyze (Optional):** Go to the 'Analysis' tab, select the desired 'Number of Clusters', and click 'Run Clustering'. View the resulting plot.
6.  **View Tables:** Go to the 'Tables' tab to see numeric summaries corresponding to the plots.
7.  **Export:** Use the download buttons on the plot or table tabs to save outputs locally.

# Availability

RoBVis is available as an open-source R Shiny application.

* **Source Code:** [https://github.com/mahmood789/786ROBmetaapp](https://github.com/mahmood789/786ROBmetaapp)
* **License:** Apache 2.0 License


The package dependencies required to run the application are managed using `renv` [@renv], with the specific versions recorded in the `renv.lock` file included in the repository, facilitating reproducibility.

# Acknowledgements
None

# References

In bib file
