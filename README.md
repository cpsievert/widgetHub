Just a repo for hosting an htmlwidget for debugging purposes. Here I how I use it:

```r
save_widget <- function(x, dir = ".") {
  dir <- normalizePath(dir, mustWork = T)
  owd <- setwd(dir)
  on.exit(owd, add = T)
  if (plotly:::is.plotly(x)) x <- as.widget(x)
  htmlwidgets::saveWidget(x, file = "index.html", selfcontained = FALSE)
}

library(plotly)
p <- plot_ly()
save_widget(p, "../widgetHub")
```
