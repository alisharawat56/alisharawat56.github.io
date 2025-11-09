---
name: HW5, Jekyll Webpage
tools: [Python, Altair, vega-lite]
image: assets/pngs/hw.png
description: A license dataset plotted in two ways.
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---


# Plots using Altair

## Using Altair to make a plot

### Static plot!

Plot 1 (static) : A bar chart showing the top 10 most common license types.
<vegachart schema-url="{{ site.baseurl }}/assets/json/hw_static.json" style="width: 100%"></vegachart>

The first visualization shows the top 10 most common business license types. I created a bar chart that displays the count of each license type so it is easy to compare which business activities are most frequently licensed. The x-axis encodes the number of licenses, and the y-axis encodes the license description. I used color to differentiate the bars, though the color does not represent an additional variable in this case; it is only used to make the plot visually clear. The only data transformation performed for this chart was grouping by license description and counting the number of occurrences, followed by selecting the top ten.

### Interactive plot

Plot 2 (interactive) : A bar chart showing license counts by community area, with a dropdown to filter by license type.
<vegachart schema-url="{{ site.baseurl }}/assets/json/hw_interactive.json" style="width: 100%"></vegachart>

For this visualization, I created a heatmap showing the relationship between license types and zip codes for the top 40 zip codes by total license count. The heatmap uses ordinal encodings for both axes—`Zip` on the x-axis and `License Type` on the y-axis—and a quantitative color encoding (`COUNT`) to represent the number of licenses, with a sequential blue color scheme to intuitively show higher counts with darker shades. I also included a linked bar chart showing the total number of licenses for the selected zip codes. On the data side, I cleaned the dataset by removing null values and rows with a zip code of 0, converted zip codes to strings for categorical encoding, aggregated counts of licenses by zip code and license type, and filtered to the top 40 zip codes to improve readability.

For interactivity, I implemented a brush selection on the heatmap that allows users to click and drag over a set of license-type/zip-code combinations. This selection dynamically filters the linked bar chart to display counts only for the selected area. This interactivity makes it easier for users to focus on subsets of the data, identify patterns, and compare the prevalence of licenses across specific zip codes, enhancing both clarity and engagement in exploring the dataset.

<!-- these are written in a combo of html and liquid --> 

<div class="left">
{% include elements/button.html link="https://github.com/UIUC-iSchool-DataViz/is445_data/raw/main/licenses_fall2022.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/alisharawat56/alisharawat56.github.io/blob/main/python_notebooks/inClass_week11.ipynb" text="The Analysis" %}
</div>

