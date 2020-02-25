# owf-lib-viz-timeseries #

This repository contains an inventory of time series visualization tools that
the Open Water Foundation (OWF) has evaluated for use in software applications.
The technologies are grouped by language, with focus on web application tools.
Separate repositories have been created when a library has been reviewed in more detail.

* [Time Series Graphing Requirements](#time-series-graphing-requirements)
* [Inventory - Application](#inventory-application)
* [Inventory - JavaScript](#inventory-javascript)
* [Additional Repositories](#additional-repositories)

---

## Time Series Graphing Requirements ##

The following are typical requirements for time series graphing tools:

* handle typical time series datasets consisting of date/time, value, and possibly flag
* handle different data interval (timestep) including minute, hour, day, month, year,
and also plot at irregular (sparse) date/time
* access data in standard formats such as CSV and JSON
* handle missing data values, for example blank in CSV or `NaN` in data, and gap in line graph
(don't connect line across missing value)
* display multiple time series on a graph
* display time series in different forms (point/symbol, line, bar, area, stacked area)
* provide mouse tracker to display time series values
* allow zoom and panning
* display intelligent date/time and numerical data axis labels, even when graph has been zoomed
* annotate graph with text, points, lines, or other shapes
* provide properties to customize the graph, including symbol style, font, etc.
* good performance even for large datasets (multiple years of data)

## Inventory - Application ##

| **Name/Link** | **Description** | **License** | **Status** | **Comments** |
| -- | -- | -- | -- |
| [TSTool](http://opencdss.state.co.us/opencdss/statedmi/) | Time series processing and visualization software. | GPL v3 | Active. | Application developed by OWF for the State of Colorado. |

## Inventory - JavaScript ##

| **Name/Link** | **Description** | **License** | **Status** | **OWF Repo** | **Comments** |
| -- | -- | -- | -- |
| [canvasJS](https://canvasjs.com/) | | Commercial | Active | [owf-lib-viz-canvasjs-js](https://github.com/OpenWaterFoundation/owf-lib-viz-canvasjs-js) | |
| [c3.js](https://c3js.org/) | | MIT | Active | [owf-lib-viz-c3-js](https://github.com/OpenWaterFoundation/owf-lib-viz-c3-js) | |
| [Chart.js](https://www.chartjs.org/) | | MIT | Active | [owf-lib-viz-chart-js](https://github.com/OpenWaterFoundation/owf-lib-viz-chart-js) | |
| [D3.js](https://d3js.org/) | | BSD 3 | Active | [owf-lib-viz-d3-js](https://github.com/OpenWaterFoundation/owf-lib-viz-d3-js) | |
| [dygraphs.js](http://dygraphs.com/) | | MIT | Active | [owf-lib-dygraphs-js](https://github.com/OpenWaterFoundation/owf-lib-viz-dygraphs-js) | |
| [Google Charts](https://developers.google.com/chart) | | Apache 2.0 | Active | [owf-lib-viz-google-charts-js](https://github.com/OpenWaterFoundation/owf-lib-viz-google-charts-js) | |
| [Google Fusion Tables](https://en.wikipedia.org/wiki/Google_Fusion_Tables) | | | Dead | [owf-lib-viz-google-fusion-tables](https://github.com/OpenWaterFoundation/owf-lib-viz-google-fusion-tables) | |
| [Highcharts](https://www.highcharts.com/) | | Commercial, CC for nonprofit | Active | [owf-lib-viz-highcharts-js](https://github.com/OpenWaterFoundation/owf-lib-viz-highcharts-js) | |
| [jqPlot.js](http://www.jqplot.com/) | | MIT, GPL v2| Active | [owf-lib-viz-jqplot-js](https://github.com/OpenWaterFoundation/owf-lib-viz-jqplot-js) | |
| [plotly.js](https://plot.ly/javascript/) | | MIT | Active | [owf-lib-viz-plotly-js](https://github.com/OpenWaterFoundation/owf-lib-viz-plotly-js) | |

## Additional Repositories ##

Additional OWF repositories include:

| **Repository** | **Description** |
| -- | -- |
| [`owf-lib-viz-heatmap`](https://github.com/OpenWaterFoundation/owf-lib-viz-heatmap) | Inventory of heatmap visualization tools. |
