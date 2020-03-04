# owf-lib-viz-timeseries #

This repository contains an inventory of time series visualization tools that
the Open Water Foundation (OWF) has evaluated for use in software applications.
The technologies are grouped by language, with focus on web application tools.
Separate repositories have been created when a tool has been reviewed in more detail.

* [Time Series Graphing Requirements](#time-series-graphing-requirements)
	+ [Options for Intelligent Axis Labeling](#options-for-intelligent-axis-labeling)
* [Inventory of Applications](#inventory-of-applications)
* [Inventory of JavaScript Tools](#inventory-of-javascript-tools)
* [Additional Repositories](#additional-repositories)

---

## Time Series Graphing Requirements ##

The following are typical requirements for time series graphing tools,
which may be provided at various levels by different visualization libraries and tools.

* handle typical time series datasets consisting of date/time, value, and possibly flag
	+ useful to standardize on [ISO 8601 date/time formats](https://en.wikipedia.org/wiki/ISO_8601)
	+ also need to handle date/time formats commonly used in software such as Excel
* handle different data interval (timestep) including minute, hour, day, month, year,
and also plot at irregular (sparse) date/time
	+ ideally use data values with date/time at precision that is appropriate,
	for example `YYYY-MM-DD` for daily data and `YYYY-MM` for monthly data
	+ if different interval are displayed on the same graph,
	display date/times in precision that is appropriate for each display element
* access data in standard formats such as CSV and JSON
	+ specifying metadata for time series is a challenge for formats such as CSV
		- see: http://learn.openwaterfoundation.org/owf-learn-csv/csv-syntax/#metadata-and-schema
		- see [TSTool `WriteTableToDelimitedFile`] command `OutputSchemaFile` parameter](http://opencdss.state.co.us/tstool/latest/doc-user/command-ref/WriteTableToDelimitedFile/WriteTableToDelimitedFile/)
* handle missing data values, for example blank cell in CSV or `NaN` in data files
	+ display as gap in line graph (don't connect line across missing value)
	+ display as empty cell in tabular view
* visualize time series in different forms (point/symbol, line, bar, area, stacked area, etc.)
	+ bars positioned so right edge is interval-ending date/time for value
	+ omit point, line, bar, etc. for missing value
	+ optionally label with data value flag
* display multiple time series on a graph, possibly using different graph style,
for example display some time series as lines on bar chart
* provide mouse tracker to display time series values
	+ mouse position output for x- and y-axes, with properly-formatted date/time
	+ vertical line for mouse position with highlight/label of intersecting data points
* allow panning
	+ keyboard arrow keys, page forward back, etc.
* allow zoom in and out
	+ via mouse drawing box or equivalent
	+ horizontal zoom is important - useful to keep same y-axis so relative scale of values is constant
	+ vertical zoom OK
	+ ability to rescale vertical axis, for example cases where all values are near bottom of graph
* display overview window, for example area under graph, showing current view of total period, and
possibly allow zooming and panning by interacting with the overview
* display intelligent date/time and numerical data axis labels, even when graph has been zoomed
	+ avoid difficult to read labeling such as overly precise `YYYY-MM-DD hh:mm:ss` label for
	date/times that are less precise (e.g., `YYYY-MM`)
	+ see TSTool intelligent labeling, which changes as the graph is zoomed
	+ see the [Options for Intelligent Axis Labeling](#options-for-intelligent-axis-labeling) below
* annotate graph with text, points, lines, or other shapes
* provide properties to customize the graph, including symbol style, font, etc.
* good performance even for large datasets (multiple years of data)
	+ examples in repositories listed in the inventory typically use small and large datasets
	to illustrate performance
* ability to save graph as an image file (png, etc.) and export underlying data as CSV, etc.
	+ for example, popup menu on graph with menu of options

### Options for Intelligent Axis Labeling ###

Labeling the axes of a time series graph can be challenging.
The goals of labeling are:

* display a reasonable number of labels that are not squished together or are too far apart,
at all zoom levels
* are rounded to reasonable values (e.g., example numbers ending in 0, 00, 000)
and date/times that are reasonably spaced (e.g., evenly divisible by common date/time intervals)
* maximize use of the visual space to display data (minimize whitespace)
* avoid axis label orientation that is difficult to quickly read
	* horizontal labels are easier to read
	* vertical labels are more difficult to read
	* angled labels are most difficult to read
* labels should clearly be associated with data, for example using ticks or grid lines
* if the graph is zoomed, the labels should adjust intelligently

Determining labels is impacted by:

* how much screen/page real-estate is available for the graph body and labels
* font size
* format of labels
	+ width and precision for numbers (e.g., `123.1234`), which depends on data units and value limits
	+ precision of date/time labels for data being displayed

The following are possible approaches that may be used by graphing packages in order to achieve optimal labeling.
In each case it is assumed that the tool has been passed the time series data in a consumable form.

1. Tool handles labeling, at various levels of configurability:
	1. The tool labels axes intelligently at all zoom levels, with no additional configuration.
	2. The tool provides configuration properties to help with labeling, such as number of labels desired,
	format for date-time, etc., in a general way.
	3. The tool provides configuration properties for more granular control of labels,
	for example, specifying date/time format for different zoom level
2. Tool relies on application code to determine label values, but the tool draws the labels:
	1. At each change that requires a redraw,
	the tool calls application code to determine the label values,
	for example passing the maximum and minimum data values to be labeled.
	2. Display properties are configured as in (1).
3. Tool relies on application code to determine label values and draw the labels:
	1. At each change that requires a redraw,
	the tool calls application code to determine the label values and draw the labels.
	2. This requires that the graphical objects such as canvas and available area for labels are passed to application code.
	3. Display properties may be configured as in (1).

## Inventory of Applications ##

| **Name/Link** | **Description** | **License** | **Status** | **Comments** |
| -- | -- | -- | -- | -- |
| [TSTool](http://opencdss.state.co.us/opencdss/tstool/) | Time series processing and visualization software. | GPL v3 | Active | Application developed by OWF for the State of Colorado. |

## Inventory of JavaScript Tools ##

| **Name/Link** | **Description** | **License** | **Status** | **OWF Repo** | **Comments** |
| -- | -- | -- | -- | -- | -- |
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
