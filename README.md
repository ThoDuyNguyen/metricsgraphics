metricsgraphics is an 'htmlwidget' interface to the MetricsGraphics.js D3 chart library.

The current `htmlwidget` wrapper for it is minimaly functional and does not provide support for metricsgraphics histograms and also does not really take advantage of metricsgraphics' best feature - time series charts. Both will be added in the next release and support for legends will appear shortly thereafter.

Charts look best in a Boostrap page (unless you customize your own CSS).

The following functions are implemented:

-   `mjs_plot`: Create a new metricsgraphics.js plot
-   `mjs_line`: metricsgraphics.js linechart "geom"
-   `mjs_point`: metricsgraphics.js scatterplot "geom"
-   `mjs_bar`: metricsgraphics.js bar chart "geom"
-   `mjs_axis_x`: Configure x axis ticks & limits
-   `mjs_axis_y`: Configure y axis ticks & limits
-   `mjs_labs`: Configure axis labels & plot description

### News

-   Version 0.1 released

### Installation

``` {.r}
devtools::install_github("hrbrmstr/metricsgraphics")
```

### Usage

``` {.r}
library(dplyr)
library(metricsgraphics)

tmp <- data.frame(year=seq(1790, 1970, 10), uspop=as.numeric(uspop))

tmp %>%
  mjs_plot(x=year, y=uspop) %>%
  mjs_line() %>%
  mjs_labs(title="Populations Recorded by the US Census", 
           description="This data set gives the population of the United States (in millions) as recorded by the decennial census for the period 1790–1970.")

tmp %>%
  mjs_plot(x=year, y=uspop, width=600) %>%
  mjs_line(area=TRUE) %>%
  mjs_labs(title="Populations Recorded by the US Census", 
           description="This data set gives the population of the United States (in millions) as recorded by the decennial census for the period 1790–1970.")

tmp %>% 
  mjs_plot(x=year, y=uspop, width=300, height=400) %>%
  mjs_bar() %>%
  mjs_labs(title="Sample Bar Chart")

mtcars %>% 
  mjs_plot(x=wt, y=mpg, width=400, height=300) %>%
  mjs_point(color_accessor=carb, size_accessor=carb) %>%
  mjs_labs(x="Weight of Car", y="Miles per Gallon", title="Scatterplot w/color & size")


mtcars %>% 
  mjs_plot(x=wt, y=mpg, width=400, height=300) %>%
  mjs_point(least_squares=TRUE) %>%
  mjs_labs(x="Weight of Car", y="Miles per Gallon", title="Scatterplot w/least squares")
```