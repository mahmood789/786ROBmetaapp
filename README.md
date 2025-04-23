# 786ROBmetaapp
# RoB Visualizer Shiny App

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

An interactive web application built with R Shiny and `bs4Dash` for conducting and visualizing Risk of Bias (RoB) assessments from systematic reviews.

## Features

* Supports data entry and visualization for multiple RoB assessment tools: ROB2, ROBINS-I, QUADAS-2, ROB1, and NOS.
* Generates standard RoB visualizations:
    * Summary Plot (stacked bar chart showing percentage of judgments per domain)
    * Traffic Light Plot (grid showing judgment for each study across domains)
    * Frequency Distribution Plot (bar charts showing counts per judgment level for each domain)
* Includes exploratory K-means clustering of studies based on RoB judgments.
* Allows data upload via CSV or Excel files.
* Includes built-in sample datasets for each supported tool.
* Provides interactive tables (`DT`) and plots (`plotly`).
* Allows downloading of plots (PNG) and summary tables (CSV/Excel).
* Provides a basic text report download summarizing the data.

## Installation

1.  **Prerequisites:**
    * R (version 4.0.0 or later recommended).
    * Git (for cloning the repository).

2.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/mahmood789/786ROBmetaapp.git](https://github.com/mahmood789/786ROBmetaapp.git)
    cd 786ROBmetaapp
    ```

3.  **Install Dependencies using `renv`:** This project uses `renv` for reproducible package management. The necessary package versions are recorded in the `renv.lock` file. *(Note: You need to run `renv::init()` or `renv::snapshot()` first in your project to create/update the `renv.lock` file if you haven't already).*
    * Open R **within the project directory** (`786ROBmetaapp`).
    * Run the following command in the R console:
        ```R
        # Install renv if you don't have it
        # install.packages("renv")

        # Restore the project library
        renv::restore()
        ```
    * This command will install the packages listed in `renv.lock` into a project-specific library. Type `y` to proceed when prompted.

## Usage

Once the dependencies are installed, you can launch the application from the R console (make sure your working directory is the project's root directory, `786ROBmetaapp`):

```R
shiny::runApp()
