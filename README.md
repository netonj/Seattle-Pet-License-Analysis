# Seattle Pet Licenses: Where Are Cats Most Common?

Exploratory data analysis and visualization of active Seattle pet licenses, built with pandas and Altair. Completed for DATA 5310 (Data Visualization), Seattle University, MS in Data Science.

## Question

How do licensed dogs and cats differ across Seattle, and where in the city are cats most common?

## Result

- About 33% of licensed dogs and cats in Seattle are cats
- ZIP codes in and around downtown are 43–48% cats, 10–14 points above the city average

    - Pioneer Square/International District (98104), Belltown (98121), Downtown (98101), Eastlake (98102), South Lake Union (98109)

- Neighborhoods at the edges of the city are 22–26% cats

    - Broadview (98177), White Center (98146), Fauntleroy (98136), West Seattle (98126)

- The data does not explain why, but the pattern is consistent with apartments and smaller homes being better suited to cats

## Data

City of Seattle, Seattle Pet Licenses (dataset jguv-t9rb), Seattle Open Data Portal: https://data.seattle.gov/Community-and-Culture/Seattle-Pet-Licenses/jguv-t9rb

- About 38,000 active licenses, 7 variables (issue date, license number, name, species, primary breed, secondary breed, ZIP code)
- Only active licenses are included, so nearly all issue dates fall between late 2025 and October 2026
- The notebook reads the data directly from the portal, so no data file is needed

## Approach

1. Data wrangling

    - Kept dogs and cats only (11 goats and 3 pigs removed)
    - Removed about 275 licenses with ZIP codes outside Seattle (98101–98199)
    - Grouped the data into small summary tables (counts by day, breed, name and ZIP code) to stay under Altair's 5,000-row limit

2. Exploratory plots: species counts, licenses by month, top dog breeds, licenses per ZIP code, and a day-of-week by month heatmap
3. Preliminary plots: top dog and cat names, licenses by ZIP code and species, and monthly licenses by species
4. Refinement: three iterations of the ZIP code plot

    - Counts to percent cats per ZIP code
    - Scatter plot of ZIP code size vs. percent cats (tested and dropped)
    - Bars diverging from the citywide average

5. Final plot: diverging bar chart of each ZIP code's cat share compared with the city average, labeled with neighborhood names

Altair transforms used: `filter`, `calculate`, `aggregate`, `window` (`rank`), `bin` and `timeUnit`.

## Files

- `Week3_Homework3_PetLicenses.ipynb`: full analysis notebook with code, charts and comments

## How to run

Requires Python 3 with pandas and Altair, run in Jupyter or VS Code.

```bash
pip install pandas altair
```

Open the notebook and run all cells. The first cell downloads the data from data.seattle.gov, which takes about a minute.

The notebook uses `alt.renderers.enable('mimetype')` so charts display in VS Code. In JupyterLab or Jupyter Notebook this line can be removed.

## Limitations

- Only covers licensed pets. Cats may be licensed less often than dogs, so the true cat share could be higher
- Active licenses only, so new pets and renewals cannot be separated
- Neighborhood names are approximate labels for ZIP codes

## Author

Jack Neton
GitHub: [netonj](https://github.com/netonj) · LinkedIn: [jackneton](https://www.linkedin.com/in/jackneton)
