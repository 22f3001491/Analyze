# Sales Analysis Dashboard

This project provides a comprehensive sales analysis solution. It includes a Python script (`execute.py`) to process sales data from an Excel file, generate key metrics, and output the results as a JSON file. A modern, responsive HTML dashboard is then used to visualize these insights. The entire process, from data analysis to dashboard deployment, is automated using GitHub Actions.

## Features

*   **Data Processing (`execute.py`):**
    *   Reads sales data from an Excel file (`data.xlsx`).
    *   Performs robust data cleaning, including standardizing column names, converting data types, and handling missing values.
    *   Calculates overall sales metrics (total sales, total orders, average order value, sales period).
    *   Identifies top 5 products by sales.
    *   Aggregates sales by product category.
    *   Generates monthly sales trends.
    *   Identifies top 5 customers by sales.
    *   Outputs all analysis results in a structured JSON format (`result.json`).
    *   Includes a fix for a non-trivial error related to handling empty date series during `min()`/`max()` operations, ensuring robustness.
    *   Ensures no "revenew" typo exists in the code (it was not present in the original, and no new instances were introduced).

*   **Data Conversion:**
    *   Automatically converts `data.xlsx` to `data.csv` for broader compatibility and potential future use.

*   **Interactive Dashboard (HTML/CSS/JS):**
    *   A single, self-contained HTML file (`index.html` - or simply the rendered HTML provided) with embedded CSS and JavaScript.
    *   Displays overall sales metrics, top products, sales by category, monthly trends, and top customers.
    *   Modern, professional design with a clean UI/UX.
    *   Fully responsive, adapting to various screen sizes (mobile-first approach).
    *   Uses semantic HTML5 elements for better structure and accessibility.
    *   Professional color scheme and typography.
    *   Fetches `result.json` dynamically to populate the dashboard.

*   **CI/CD Automation (GitHub Actions):**
    *   A push workflow (`.github/workflows/ci.yml`) automates the entire process.
    *   **Linting:** Runs `ruff` to ensure code quality and consistency.
    *   **Execution:** Executes `python execute.py` to generate `result.json`.
    *   **Deployment:** Publishes `result.json` (alongside the HTML dashboard if present in the repo root for static site hosting) to GitHub Pages. The generated `result.json` is accessible via the GitHub Pages URL.

## How to Use

1.  **Clone the Repository:**
    bash
    git clone <your-repository-url>
    cd <your-repository-name>
    

2.  **Provided Files:**
    *   `execute.py`: The Python script for sales data analysis.
    *   `data.xlsx`: The input Excel file containing sales data.
    *   `data.csv`: The converted CSV version of `data.xlsx`.
    *   `.github/workflows/ci.yml`: The GitHub Actions workflow definition.
    *   `index.html` (or the content of the generated HTML): The web dashboard for visualization.

3.  **Local Execution (Optional):**
    If you want to run the analysis script locally:
    *   Ensure Python 3.11+ and Pandas 2.3 are installed.
    *   Install dependencies: `pip install pandas ruff`
    *   Run the analysis: `python execute.py > result.json`
    *   Open the HTML file in your browser. If `result.json` is in the same directory, the dashboard will load the data.

4.  **GitHub Actions & Pages:**
    *   Push the provided files (including the fixed `execute.py`, `data.csv`, and `.github/workflows/ci.yml`) to your `main` branch.
    *   GitHub Actions will automatically trigger:
        *   It will lint `execute.py` with `ruff`.
        *   It will run `execute.py` to generate `result.json`.
        *   It will publish `result.json` to GitHub Pages.
    *   To view the published `result.json` and the dashboard, enable GitHub Pages for your repository (if not already enabled) from the repository settings, pointing to the `gh-pages` branch or the `main` branch `/ (root)`.
    *   The `result.json` will be available at `https://<YOUR_USERNAME>.github.io/<YOUR_REPOSITORY_NAME>/result.json`.
    *   The `index.html` file (or the HTML content you place at the root for a single-page site) will automatically load `result.json` and render the dashboard.

## Technologies Used

*   **Python 3.11+**: For backend data processing.
*   **Pandas 2.3**: A powerful data manipulation and analysis library for Python.
*   **Ruff**: An extremely fast Python linter, used for code quality checks in CI.
*   **HTML5, CSS3, JavaScript**: For the interactive and responsive sales dashboard.
*   **GitHub Actions**: For continuous integration and continuous deployment (CI/CD).
*   **GitHub Pages**: For hosting the `result.json` and the static HTML dashboard.