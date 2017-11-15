---
title: "Reproducible Research: Peer Assessment 1"
author: "Fabio Paderi"
date: "2017-15-11"
output: 
  html_document:
    keep_md: true
---

### Set options


```r
knitr::opts_chunk$set(echo = TRUE, message = FALSE, warning = FALSE,
                      comment = NA)
```

### Load required packages



```r
library(dplyr)
library(lubridate)
library(ggplot2)
library(knitr)
library(plotly)
```

### Load the data


```r
activity <- read.csv("activity.csv",header = TRUE)
## transform in date
activity$date <- ymd(activity$date)
```

### What is mean total number of steps taken per day?  
#### Histogram of the total number of steps taken each day

```r
bydate = activity %>%
    group_by(date) %>%
    summarise(N = n(), Total_steps = sum(steps, na.rm = TRUE))

a <- ggplot(bydate, aes(x = Total_steps)) + geom_histogram(fill = "#A6CEE3", bins = 30, col = "#1F78B4") +
    ggtitle("Total number of steps Taken each day")
ggplotly(a)
```

<!--html_preserve--><div id="cac4d345158" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="cac4d345158">{"x":{"data":[{"orientation":"v","width":[730.827586206897,730.827586206896,730.827586206896,730.827586206897,730.827586206897,730.827586206896,730.827586206897,730.827586206897,730.827586206897,730.827586206897,730.827586206895,730.827586206897,730.827586206899,730.827586206899,730.827586206899,730.827586206899,730.827586206899,730.827586206899,730.827586206899,730.827586206899,730.827586206895,730.827586206899,730.827586206895,730.827586206899,730.827586206899,730.827586206899,730.827586206899,730.827586206899,730.827586206899,730.827586206899],"base":[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],"x":[0,730.827586206897,1461.65517241379,2192.48275862069,2923.31034482759,3654.13793103448,4384.96551724138,5115.79310344828,5846.62068965517,6577.44827586207,7308.27586206897,8039.10344827586,8769.93103448276,9500.75862068966,10231.5862068966,10962.4137931034,11693.2413793103,12424.0689655172,13154.8965517241,13885.724137931,14616.5517241379,15347.3793103448,16078.2068965517,16809.0344827586,17539.8620689655,18270.6896551724,19001.5172413793,19732.3448275862,20463.1724137931,21194],"y":[10,0,0,1,1,0,1,2,0,1,2,2,3,1,9,4,4,4,5,1,2,5,0,0,1,0,0,0,1,1],"text":["count: 10<br />Total_steps:     0.0000","count:  0<br />Total_steps:   730.8276","count:  0<br />Total_steps:  1461.6552","count:  1<br />Total_steps:  2192.4828","count:  1<br />Total_steps:  2923.3103","count:  0<br />Total_steps:  3654.1379","count:  1<br />Total_steps:  4384.9655","count:  2<br />Total_steps:  5115.7931","count:  0<br />Total_steps:  5846.6207","count:  1<br />Total_steps:  6577.4483","count:  2<br />Total_steps:  7308.2759","count:  2<br />Total_steps:  8039.1034","count:  3<br />Total_steps:  8769.9310","count:  1<br />Total_steps:  9500.7586","count:  9<br />Total_steps: 10231.5862","count:  4<br />Total_steps: 10962.4138","count:  4<br />Total_steps: 11693.2414","count:  4<br />Total_steps: 12424.0690","count:  5<br />Total_steps: 13154.8966","count:  1<br />Total_steps: 13885.7241","count:  2<br />Total_steps: 14616.5517","count:  5<br />Total_steps: 15347.3793","count:  0<br />Total_steps: 16078.2069","count:  0<br />Total_steps: 16809.0345","count:  1<br />Total_steps: 17539.8621","count:  0<br />Total_steps: 18270.6897","count:  0<br />Total_steps: 19001.5172","count:  0<br />Total_steps: 19732.3448","count:  1<br />Total_steps: 20463.1724","count:  1<br />Total_steps: 21194.0000"],"type":"bar","marker":{"autocolorscale":false,"color":"rgba(166,206,227,1)","line":{"width":1.88976377952756,"color":"rgba(31,120,180,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":48.9497716894977},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":"Total number of steps Taken each day","titlefont":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"xaxis":{"domain":[0,1],"type":"linear","autorange":false,"tickmode":"array","range":[-1461.65517241379,22655.6551724138],"ticktext":["0","5000","10000","15000","20000"],"tickvals":[0,5000,10000,15000,20000],"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":"Total_steps","titlefont":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"type":"linear","autorange":false,"tickmode":"array","range":[-0.5,10.5],"ticktext":["0.0","2.5","5.0","7.5","10.0"],"tickvals":[0,2.5,5,7.5,10],"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":"count","titlefont":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"barmode":"stack","bargap":0,"hovermode":"closest"},"source":"A","attrs":{"cac23f396d8":{"x":{},"type":"ggplotly"}},"cur_data":"cac23f396d8","visdat":{"cac23f396d8":["function (y) ","x"]},"config":{"modeBarButtonsToAdd":[{"name":"Collaborate","icon":{"width":1000,"ascent":500,"descent":-50,"path":"M487 375c7-10 9-23 5-36l-79-259c-3-12-11-23-22-31-11-8-22-12-35-12l-263 0c-15 0-29 5-43 15-13 10-23 23-28 37-5 13-5 25-1 37 0 0 0 3 1 7 1 5 1 8 1 11 0 2 0 4-1 6 0 3-1 5-1 6 1 2 2 4 3 6 1 2 2 4 4 6 2 3 4 5 5 7 5 7 9 16 13 26 4 10 7 19 9 26 0 2 0 5 0 9-1 4-1 6 0 8 0 2 2 5 4 8 3 3 5 5 5 7 4 6 8 15 12 26 4 11 7 19 7 26 1 1 0 4 0 9-1 4-1 7 0 8 1 2 3 5 6 8 4 4 6 6 6 7 4 5 8 13 13 24 4 11 7 20 7 28 1 1 0 4 0 7-1 3-1 6-1 7 0 2 1 4 3 6 1 1 3 4 5 6 2 3 3 5 5 6 1 2 3 5 4 9 2 3 3 7 5 10 1 3 2 6 4 10 2 4 4 7 6 9 2 3 4 5 7 7 3 2 7 3 11 3 3 0 8 0 13-1l0-1c7 2 12 2 14 2l218 0c14 0 25-5 32-16 8-10 10-23 6-37l-79-259c-7-22-13-37-20-43-7-7-19-10-37-10l-248 0c-5 0-9-2-11-5-2-3-2-7 0-12 4-13 18-20 41-20l264 0c5 0 10 2 16 5 5 3 8 6 10 11l85 282c2 5 2 10 2 17 7-3 13-7 17-13z m-304 0c-1-3-1-5 0-7 1-1 3-2 6-2l174 0c2 0 4 1 7 2 2 2 4 4 5 7l6 18c0 3 0 5-1 7-1 1-3 2-6 2l-173 0c-3 0-5-1-8-2-2-2-4-4-4-7z m-24-73c-1-3-1-5 0-7 2-2 3-2 6-2l174 0c2 0 5 0 7 2 3 2 4 4 5 7l6 18c1 2 0 5-1 6-1 2-3 3-5 3l-174 0c-3 0-5-1-7-3-3-1-4-4-5-6z"},"click":"function(gd) { \n        // is this being viewed in RStudio?\n        if (location.search == '?viewer_pane=1') {\n          alert('To learn about plotly for collaboration, visit:\\n https://cpsievert.github.io/plotly_book/plot-ly-for-collaboration.html');\n        } else {\n          window.open('https://cpsievert.github.io/plotly_book/plot-ly-for-collaboration.html', '_blank');\n        }\n      }"}],"cloud":false},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1}},"base_url":"https://plot.ly"},"evals":["config.modeBarButtonsToAdd.0.click"],"jsHooks":{"render":[{"code":"function(el, x) { var ctConfig = crosstalk.var('plotlyCrosstalkOpts').set({\"on\":\"plotly_click\",\"persistent\":false,\"dynamic\":false,\"selectize\":false,\"opacityDim\":0.2,\"selected\":{\"opacity\":1}}); }","data":null}]}}</script><!--/html_preserve-->

#### Mean and median number of steps taken each day

```r
steps_summary <- bydate %>%
    summarise(Mean_steps = mean(Total_steps, na.rm = TRUE),
              Median_steps = median(Total_steps, na.rm = TRUE))

kable(steps_summary, align = 'l')
```



Mean_steps   Median_steps 
-----------  -------------
9354.23      10395        

### What is the average daily activity pattern?  
#### Time series plot of the average number of steps taken


```r
by_interval = activity %>%
    group_by(interval) %>%
    summarise(Mean_steps = mean(steps, na.rm = TRUE))
    
b <- ggplot(by_interval, aes( x = interval, y = Mean_steps)) + geom_path() +
    labs(x = "5-minute intervals", title = "Average of steps taken across 5-minutes interval")
ggplotly(b)
```

<!--html_preserve--><div id="cac78e61997" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="cac78e61997">{"x":{"data":[{"x":[0,5,10,15,20,25,30,35,40,45,50,55,100,105,110,115,120,125,130,135,140,145,150,155,200,205,210,215,220,225,230,235,240,245,250,255,300,305,310,315,320,325,330,335,340,345,350,355,400,405,410,415,420,425,430,435,440,445,450,455,500,505,510,515,520,525,530,535,540,545,550,555,600,605,610,615,620,625,630,635,640,645,650,655,700,705,710,715,720,725,730,735,740,745,750,755,800,805,810,815,820,825,830,835,840,845,850,855,900,905,910,915,920,925,930,935,940,945,950,955,1000,1005,1010,1015,1020,1025,1030,1035,1040,1045,1050,1055,1100,1105,1110,1115,1120,1125,1130,1135,1140,1145,1150,1155,1200,1205,1210,1215,1220,1225,1230,1235,1240,1245,1250,1255,1300,1305,1310,1315,1320,1325,1330,1335,1340,1345,1350,1355,1400,1405,1410,1415,1420,1425,1430,1435,1440,1445,1450,1455,1500,1505,1510,1515,1520,1525,1530,1535,1540,1545,1550,1555,1600,1605,1610,1615,1620,1625,1630,1635,1640,1645,1650,1655,1700,1705,1710,1715,1720,1725,1730,1735,1740,1745,1750,1755,1800,1805,1810,1815,1820,1825,1830,1835,1840,1845,1850,1855,1900,1905,1910,1915,1920,1925,1930,1935,1940,1945,1950,1955,2000,2005,2010,2015,2020,2025,2030,2035,2040,2045,2050,2055,2100,2105,2110,2115,2120,2125,2130,2135,2140,2145,2150,2155,2200,2205,2210,2215,2220,2225,2230,2235,2240,2245,2250,2255,2300,2305,2310,2315,2320,2325,2330,2335,2340,2345,2350,2355],"y":[1.71698113207547,0.339622641509434,0.132075471698113,0.150943396226415,0.0754716981132075,2.09433962264151,0.528301886792453,0.867924528301887,0,1.47169811320755,0.30188679245283,0.132075471698113,0.320754716981132,0.679245283018868,0.150943396226415,0.339622641509434,0,1.11320754716981,1.83018867924528,0.169811320754717,0.169811320754717,0.377358490566038,0.264150943396226,0,0,0,1.13207547169811,0,0,0.132075471698113,0,0.226415094339623,0,0,1.54716981132075,0.943396226415094,0,0,0,0,0.207547169811321,0.622641509433962,1.62264150943396,0.584905660377358,0.490566037735849,0.0754716981132075,0,0,1.18867924528302,0.943396226415094,2.56603773584906,0,0.339622641509434,0.358490566037736,4.11320754716981,0.660377358490566,3.49056603773585,0.830188679245283,3.11320754716981,1.11320754716981,0,1.56603773584906,3,2.24528301886792,3.32075471698113,2.9622641509434,2.09433962264151,6.05660377358491,16.0188679245283,18.3396226415094,39.4528301886792,44.4905660377358,31.4905660377358,49.2641509433962,53.7735849056604,63.4528301886792,49.9622641509434,47.0754716981132,52.1509433962264,39.3396226415094,44.0188679245283,44.1698113207547,37.3584905660377,49.0377358490566,43.811320754717,44.377358490566,50.5094339622642,54.5094339622642,49.9245283018868,50.9811320754717,55.6792452830189,44.3207547169811,52.2641509433962,69.5471698113208,57.8490566037736,56.1509433962264,73.377358490566,68.2075471698113,129.433962264151,157.528301886792,171.150943396226,155.396226415094,177.301886792453,206.169811320755,195.924528301887,179.566037735849,183.396226415094,167.018867924528,143.452830188679,124.037735849057,109.11320754717,108.11320754717,103.716981132075,95.9622641509434,66.2075471698113,45.2264150943396,24.7924528301887,38.7547169811321,34.9811320754717,21.0566037735849,40.5660377358491,26.9811320754717,42.4150943396226,52.6603773584906,38.9245283018868,50.7924528301887,44.2830188679245,37.4150943396226,34.6981132075472,28.3396226415094,25.0943396226415,31.9433962264151,31.3584905660377,29.6792452830189,21.3207547169811,25.5471698113208,28.377358490566,26.4716981132075,33.4339622641509,49.9811320754717,42.0377358490566,44.6037735849057,46.0377358490566,59.188679245283,63.8679245283019,87.6981132075472,94.8490566037736,92.7735849056604,63.3962264150943,50.1698113207547,54.4716981132075,32.4150943396226,26.5283018867925,37.7358490566038,45.0566037735849,67.2830188679245,42.3396226415094,39.8867924528302,43.2641509433962,40.9811320754717,46.2452830188679,56.4339622641509,42.7547169811321,25.1320754716981,39.9622641509434,53.5471698113208,47.3207547169811,60.811320754717,55.7547169811321,51.9622641509434,43.5849056603774,48.6981132075472,35.4716981132075,37.5471698113208,41.8490566037736,27.5094339622642,17.1132075471698,26.0754716981132,43.622641509434,43.7735849056604,30.0188679245283,36.0754716981132,35.4905660377358,38.8490566037736,45.9622641509434,47.7547169811321,48.1320754716981,65.3207547169811,82.9056603773585,98.6603773584906,102.11320754717,83.9622641509434,62.1320754716981,64.1320754716981,74.5471698113208,63.1698113207547,56.9056603773585,59.7735849056604,43.8679245283019,38.5660377358491,44.6603773584906,45.4528301886792,46.2075471698113,43.6792452830189,46.622641509434,56.3018867924528,50.7169811320755,61.2264150943396,72.7169811320755,78.9433962264151,68.9433962264151,59.6603773584906,75.0943396226415,56.5094339622642,34.7735849056604,37.4528301886792,40.6792452830189,58.0188679245283,74.6981132075472,85.3207547169811,59.2641509433962,67.7735849056604,77.6981132075472,74.2452830188679,85.3396226415094,99.4528301886792,86.5849056603774,85.6037735849057,84.8679245283019,77.8301886792453,58.0377358490566,53.3584905660377,36.3207547169811,20.7169811320755,27.3962264150943,40.0188679245283,30.2075471698113,25.5471698113208,45.6603773584906,33.5283018867925,19.622641509434,19.0188679245283,19.3396226415094,33.3396226415094,26.811320754717,21.1698113207547,27.3018867924528,21.3396226415094,19.5471698113208,21.3207547169811,32.3018867924528,20.1509433962264,15.9433962264151,17.2264150943396,23.4528301886792,19.2452830188679,12.4528301886792,8.0188679245283,14.6603773584906,16.3018867924528,8.67924528301887,7.79245283018868,8.13207547169811,2.62264150943396,1.45283018867925,3.67924528301887,4.81132075471698,8.50943396226415,7.07547169811321,8.69811320754717,9.75471698113208,2.20754716981132,0.320754716981132,0.113207547169811,1.60377358490566,4.60377358490566,3.30188679245283,2.84905660377358,0,0.830188679245283,0.962264150943396,1.58490566037736,2.60377358490566,4.69811320754717,3.30188679245283,0.641509433962264,0.226415094339623,1.07547169811321],"text":["interval:    0<br />Mean_steps:   1.7169811","interval:    5<br />Mean_steps:   0.3396226","interval:   10<br />Mean_steps:   0.1320755","interval:   15<br />Mean_steps:   0.1509434","interval:   20<br />Mean_steps:   0.0754717","interval:   25<br />Mean_steps:   2.0943396","interval:   30<br />Mean_steps:   0.5283019","interval:   35<br />Mean_steps:   0.8679245","interval:   40<br />Mean_steps:   0.0000000","interval:   45<br />Mean_steps:   1.4716981","interval:   50<br />Mean_steps:   0.3018868","interval:   55<br />Mean_steps:   0.1320755","interval:  100<br />Mean_steps:   0.3207547","interval:  105<br />Mean_steps:   0.6792453","interval:  110<br />Mean_steps:   0.1509434","interval:  115<br />Mean_steps:   0.3396226","interval:  120<br />Mean_steps:   0.0000000","interval:  125<br />Mean_steps:   1.1132075","interval:  130<br />Mean_steps:   1.8301887","interval:  135<br />Mean_steps:   0.1698113","interval:  140<br />Mean_steps:   0.1698113","interval:  145<br />Mean_steps:   0.3773585","interval:  150<br />Mean_steps:   0.2641509","interval:  155<br />Mean_steps:   0.0000000","interval:  200<br />Mean_steps:   0.0000000","interval:  205<br />Mean_steps:   0.0000000","interval:  210<br />Mean_steps:   1.1320755","interval:  215<br />Mean_steps:   0.0000000","interval:  220<br />Mean_steps:   0.0000000","interval:  225<br />Mean_steps:   0.1320755","interval:  230<br />Mean_steps:   0.0000000","interval:  235<br />Mean_steps:   0.2264151","interval:  240<br />Mean_steps:   0.0000000","interval:  245<br />Mean_steps:   0.0000000","interval:  250<br />Mean_steps:   1.5471698","interval:  255<br />Mean_steps:   0.9433962","interval:  300<br />Mean_steps:   0.0000000","interval:  305<br />Mean_steps:   0.0000000","interval:  310<br />Mean_steps:   0.0000000","interval:  315<br />Mean_steps:   0.0000000","interval:  320<br />Mean_steps:   0.2075472","interval:  325<br />Mean_steps:   0.6226415","interval:  330<br />Mean_steps:   1.6226415","interval:  335<br />Mean_steps:   0.5849057","interval:  340<br />Mean_steps:   0.4905660","interval:  345<br />Mean_steps:   0.0754717","interval:  350<br />Mean_steps:   0.0000000","interval:  355<br />Mean_steps:   0.0000000","interval:  400<br />Mean_steps:   1.1886792","interval:  405<br />Mean_steps:   0.9433962","interval:  410<br />Mean_steps:   2.5660377","interval:  415<br />Mean_steps:   0.0000000","interval:  420<br />Mean_steps:   0.3396226","interval:  425<br />Mean_steps:   0.3584906","interval:  430<br />Mean_steps:   4.1132075","interval:  435<br />Mean_steps:   0.6603774","interval:  440<br />Mean_steps:   3.4905660","interval:  445<br />Mean_steps:   0.8301887","interval:  450<br />Mean_steps:   3.1132075","interval:  455<br />Mean_steps:   1.1132075","interval:  500<br />Mean_steps:   0.0000000","interval:  505<br />Mean_steps:   1.5660377","interval:  510<br />Mean_steps:   3.0000000","interval:  515<br />Mean_steps:   2.2452830","interval:  520<br />Mean_steps:   3.3207547","interval:  525<br />Mean_steps:   2.9622642","interval:  530<br />Mean_steps:   2.0943396","interval:  535<br />Mean_steps:   6.0566038","interval:  540<br />Mean_steps:  16.0188679","interval:  545<br />Mean_steps:  18.3396226","interval:  550<br />Mean_steps:  39.4528302","interval:  555<br />Mean_steps:  44.4905660","interval:  600<br />Mean_steps:  31.4905660","interval:  605<br />Mean_steps:  49.2641509","interval:  610<br />Mean_steps:  53.7735849","interval:  615<br />Mean_steps:  63.4528302","interval:  620<br />Mean_steps:  49.9622642","interval:  625<br />Mean_steps:  47.0754717","interval:  630<br />Mean_steps:  52.1509434","interval:  635<br />Mean_steps:  39.3396226","interval:  640<br />Mean_steps:  44.0188679","interval:  645<br />Mean_steps:  44.1698113","interval:  650<br />Mean_steps:  37.3584906","interval:  655<br />Mean_steps:  49.0377358","interval:  700<br />Mean_steps:  43.8113208","interval:  705<br />Mean_steps:  44.3773585","interval:  710<br />Mean_steps:  50.5094340","interval:  715<br />Mean_steps:  54.5094340","interval:  720<br />Mean_steps:  49.9245283","interval:  725<br />Mean_steps:  50.9811321","interval:  730<br />Mean_steps:  55.6792453","interval:  735<br />Mean_steps:  44.3207547","interval:  740<br />Mean_steps:  52.2641509","interval:  745<br />Mean_steps:  69.5471698","interval:  750<br />Mean_steps:  57.8490566","interval:  755<br />Mean_steps:  56.1509434","interval:  800<br />Mean_steps:  73.3773585","interval:  805<br />Mean_steps:  68.2075472","interval:  810<br />Mean_steps: 129.4339623","interval:  815<br />Mean_steps: 157.5283019","interval:  820<br />Mean_steps: 171.1509434","interval:  825<br />Mean_steps: 155.3962264","interval:  830<br />Mean_steps: 177.3018868","interval:  835<br />Mean_steps: 206.1698113","interval:  840<br />Mean_steps: 195.9245283","interval:  845<br />Mean_steps: 179.5660377","interval:  850<br />Mean_steps: 183.3962264","interval:  855<br />Mean_steps: 167.0188679","interval:  900<br />Mean_steps: 143.4528302","interval:  905<br />Mean_steps: 124.0377358","interval:  910<br />Mean_steps: 109.1132075","interval:  915<br />Mean_steps: 108.1132075","interval:  920<br />Mean_steps: 103.7169811","interval:  925<br />Mean_steps:  95.9622642","interval:  930<br />Mean_steps:  66.2075472","interval:  935<br />Mean_steps:  45.2264151","interval:  940<br />Mean_steps:  24.7924528","interval:  945<br />Mean_steps:  38.7547170","interval:  950<br />Mean_steps:  34.9811321","interval:  955<br />Mean_steps:  21.0566038","interval: 1000<br />Mean_steps:  40.5660377","interval: 1005<br />Mean_steps:  26.9811321","interval: 1010<br />Mean_steps:  42.4150943","interval: 1015<br />Mean_steps:  52.6603774","interval: 1020<br />Mean_steps:  38.9245283","interval: 1025<br />Mean_steps:  50.7924528","interval: 1030<br />Mean_steps:  44.2830189","interval: 1035<br />Mean_steps:  37.4150943","interval: 1040<br />Mean_steps:  34.6981132","interval: 1045<br />Mean_steps:  28.3396226","interval: 1050<br />Mean_steps:  25.0943396","interval: 1055<br />Mean_steps:  31.9433962","interval: 1100<br />Mean_steps:  31.3584906","interval: 1105<br />Mean_steps:  29.6792453","interval: 1110<br />Mean_steps:  21.3207547","interval: 1115<br />Mean_steps:  25.5471698","interval: 1120<br />Mean_steps:  28.3773585","interval: 1125<br />Mean_steps:  26.4716981","interval: 1130<br />Mean_steps:  33.4339623","interval: 1135<br />Mean_steps:  49.9811321","interval: 1140<br />Mean_steps:  42.0377358","interval: 1145<br />Mean_steps:  44.6037736","interval: 1150<br />Mean_steps:  46.0377358","interval: 1155<br />Mean_steps:  59.1886792","interval: 1200<br />Mean_steps:  63.8679245","interval: 1205<br />Mean_steps:  87.6981132","interval: 1210<br />Mean_steps:  94.8490566","interval: 1215<br />Mean_steps:  92.7735849","interval: 1220<br />Mean_steps:  63.3962264","interval: 1225<br />Mean_steps:  50.1698113","interval: 1230<br />Mean_steps:  54.4716981","interval: 1235<br />Mean_steps:  32.4150943","interval: 1240<br />Mean_steps:  26.5283019","interval: 1245<br />Mean_steps:  37.7358491","interval: 1250<br />Mean_steps:  45.0566038","interval: 1255<br />Mean_steps:  67.2830189","interval: 1300<br />Mean_steps:  42.3396226","interval: 1305<br />Mean_steps:  39.8867925","interval: 1310<br />Mean_steps:  43.2641509","interval: 1315<br />Mean_steps:  40.9811321","interval: 1320<br />Mean_steps:  46.2452830","interval: 1325<br />Mean_steps:  56.4339623","interval: 1330<br />Mean_steps:  42.7547170","interval: 1335<br />Mean_steps:  25.1320755","interval: 1340<br />Mean_steps:  39.9622642","interval: 1345<br />Mean_steps:  53.5471698","interval: 1350<br />Mean_steps:  47.3207547","interval: 1355<br />Mean_steps:  60.8113208","interval: 1400<br />Mean_steps:  55.7547170","interval: 1405<br />Mean_steps:  51.9622642","interval: 1410<br />Mean_steps:  43.5849057","interval: 1415<br />Mean_steps:  48.6981132","interval: 1420<br />Mean_steps:  35.4716981","interval: 1425<br />Mean_steps:  37.5471698","interval: 1430<br />Mean_steps:  41.8490566","interval: 1435<br />Mean_steps:  27.5094340","interval: 1440<br />Mean_steps:  17.1132075","interval: 1445<br />Mean_steps:  26.0754717","interval: 1450<br />Mean_steps:  43.6226415","interval: 1455<br />Mean_steps:  43.7735849","interval: 1500<br />Mean_steps:  30.0188679","interval: 1505<br />Mean_steps:  36.0754717","interval: 1510<br />Mean_steps:  35.4905660","interval: 1515<br />Mean_steps:  38.8490566","interval: 1520<br />Mean_steps:  45.9622642","interval: 1525<br />Mean_steps:  47.7547170","interval: 1530<br />Mean_steps:  48.1320755","interval: 1535<br />Mean_steps:  65.3207547","interval: 1540<br />Mean_steps:  82.9056604","interval: 1545<br />Mean_steps:  98.6603774","interval: 1550<br />Mean_steps: 102.1132075","interval: 1555<br />Mean_steps:  83.9622642","interval: 1600<br />Mean_steps:  62.1320755","interval: 1605<br />Mean_steps:  64.1320755","interval: 1610<br />Mean_steps:  74.5471698","interval: 1615<br />Mean_steps:  63.1698113","interval: 1620<br />Mean_steps:  56.9056604","interval: 1625<br />Mean_steps:  59.7735849","interval: 1630<br />Mean_steps:  43.8679245","interval: 1635<br />Mean_steps:  38.5660377","interval: 1640<br />Mean_steps:  44.6603774","interval: 1645<br />Mean_steps:  45.4528302","interval: 1650<br />Mean_steps:  46.2075472","interval: 1655<br />Mean_steps:  43.6792453","interval: 1700<br />Mean_steps:  46.6226415","interval: 1705<br />Mean_steps:  56.3018868","interval: 1710<br />Mean_steps:  50.7169811","interval: 1715<br />Mean_steps:  61.2264151","interval: 1720<br />Mean_steps:  72.7169811","interval: 1725<br />Mean_steps:  78.9433962","interval: 1730<br />Mean_steps:  68.9433962","interval: 1735<br />Mean_steps:  59.6603774","interval: 1740<br />Mean_steps:  75.0943396","interval: 1745<br />Mean_steps:  56.5094340","interval: 1750<br />Mean_steps:  34.7735849","interval: 1755<br />Mean_steps:  37.4528302","interval: 1800<br />Mean_steps:  40.6792453","interval: 1805<br />Mean_steps:  58.0188679","interval: 1810<br />Mean_steps:  74.6981132","interval: 1815<br />Mean_steps:  85.3207547","interval: 1820<br />Mean_steps:  59.2641509","interval: 1825<br />Mean_steps:  67.7735849","interval: 1830<br />Mean_steps:  77.6981132","interval: 1835<br />Mean_steps:  74.2452830","interval: 1840<br />Mean_steps:  85.3396226","interval: 1845<br />Mean_steps:  99.4528302","interval: 1850<br />Mean_steps:  86.5849057","interval: 1855<br />Mean_steps:  85.6037736","interval: 1900<br />Mean_steps:  84.8679245","interval: 1905<br />Mean_steps:  77.8301887","interval: 1910<br />Mean_steps:  58.0377358","interval: 1915<br />Mean_steps:  53.3584906","interval: 1920<br />Mean_steps:  36.3207547","interval: 1925<br />Mean_steps:  20.7169811","interval: 1930<br />Mean_steps:  27.3962264","interval: 1935<br />Mean_steps:  40.0188679","interval: 1940<br />Mean_steps:  30.2075472","interval: 1945<br />Mean_steps:  25.5471698","interval: 1950<br />Mean_steps:  45.6603774","interval: 1955<br />Mean_steps:  33.5283019","interval: 2000<br />Mean_steps:  19.6226415","interval: 2005<br />Mean_steps:  19.0188679","interval: 2010<br />Mean_steps:  19.3396226","interval: 2015<br />Mean_steps:  33.3396226","interval: 2020<br />Mean_steps:  26.8113208","interval: 2025<br />Mean_steps:  21.1698113","interval: 2030<br />Mean_steps:  27.3018868","interval: 2035<br />Mean_steps:  21.3396226","interval: 2040<br />Mean_steps:  19.5471698","interval: 2045<br />Mean_steps:  21.3207547","interval: 2050<br />Mean_steps:  32.3018868","interval: 2055<br />Mean_steps:  20.1509434","interval: 2100<br />Mean_steps:  15.9433962","interval: 2105<br />Mean_steps:  17.2264151","interval: 2110<br />Mean_steps:  23.4528302","interval: 2115<br />Mean_steps:  19.2452830","interval: 2120<br />Mean_steps:  12.4528302","interval: 2125<br />Mean_steps:   8.0188679","interval: 2130<br />Mean_steps:  14.6603774","interval: 2135<br />Mean_steps:  16.3018868","interval: 2140<br />Mean_steps:   8.6792453","interval: 2145<br />Mean_steps:   7.7924528","interval: 2150<br />Mean_steps:   8.1320755","interval: 2155<br />Mean_steps:   2.6226415","interval: 2200<br />Mean_steps:   1.4528302","interval: 2205<br />Mean_steps:   3.6792453","interval: 2210<br />Mean_steps:   4.8113208","interval: 2215<br />Mean_steps:   8.5094340","interval: 2220<br />Mean_steps:   7.0754717","interval: 2225<br />Mean_steps:   8.6981132","interval: 2230<br />Mean_steps:   9.7547170","interval: 2235<br />Mean_steps:   2.2075472","interval: 2240<br />Mean_steps:   0.3207547","interval: 2245<br />Mean_steps:   0.1132075","interval: 2250<br />Mean_steps:   1.6037736","interval: 2255<br />Mean_steps:   4.6037736","interval: 2300<br />Mean_steps:   3.3018868","interval: 2305<br />Mean_steps:   2.8490566","interval: 2310<br />Mean_steps:   0.0000000","interval: 2315<br />Mean_steps:   0.8301887","interval: 2320<br />Mean_steps:   0.9622642","interval: 2325<br />Mean_steps:   1.5849057","interval: 2330<br />Mean_steps:   2.6037736","interval: 2335<br />Mean_steps:   4.6981132","interval: 2340<br />Mean_steps:   3.3018868","interval: 2345<br />Mean_steps:   0.6415094","interval: 2350<br />Mean_steps:   0.2264151","interval: 2355<br />Mean_steps:   1.0754717"],"type":"scatter","mode":"lines","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":43.1050228310502},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":"Average of steps taken across 5-minutes interval","titlefont":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"xaxis":{"domain":[0,1],"type":"linear","autorange":false,"tickmode":"array","range":[-117.75,2472.75],"ticktext":["0","500","1000","1500","2000"],"tickvals":[0,500,1000,1500,2000],"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":"5-minute intervals","titlefont":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"type":"linear","autorange":false,"tickmode":"array","range":[-10.3084905660377,216.478301886792],"ticktext":["0","50","100","150","200"],"tickvals":[0,50,100,150,200],"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":"Mean_steps","titlefont":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest"},"source":"A","attrs":{"cac539d4043":{"x":{},"y":{},"type":"ggplotly"}},"cur_data":"cac539d4043","visdat":{"cac539d4043":["function (y) ","x"]},"config":{"modeBarButtonsToAdd":[{"name":"Collaborate","icon":{"width":1000,"ascent":500,"descent":-50,"path":"M487 375c7-10 9-23 5-36l-79-259c-3-12-11-23-22-31-11-8-22-12-35-12l-263 0c-15 0-29 5-43 15-13 10-23 23-28 37-5 13-5 25-1 37 0 0 0 3 1 7 1 5 1 8 1 11 0 2 0 4-1 6 0 3-1 5-1 6 1 2 2 4 3 6 1 2 2 4 4 6 2 3 4 5 5 7 5 7 9 16 13 26 4 10 7 19 9 26 0 2 0 5 0 9-1 4-1 6 0 8 0 2 2 5 4 8 3 3 5 5 5 7 4 6 8 15 12 26 4 11 7 19 7 26 1 1 0 4 0 9-1 4-1 7 0 8 1 2 3 5 6 8 4 4 6 6 6 7 4 5 8 13 13 24 4 11 7 20 7 28 1 1 0 4 0 7-1 3-1 6-1 7 0 2 1 4 3 6 1 1 3 4 5 6 2 3 3 5 5 6 1 2 3 5 4 9 2 3 3 7 5 10 1 3 2 6 4 10 2 4 4 7 6 9 2 3 4 5 7 7 3 2 7 3 11 3 3 0 8 0 13-1l0-1c7 2 12 2 14 2l218 0c14 0 25-5 32-16 8-10 10-23 6-37l-79-259c-7-22-13-37-20-43-7-7-19-10-37-10l-248 0c-5 0-9-2-11-5-2-3-2-7 0-12 4-13 18-20 41-20l264 0c5 0 10 2 16 5 5 3 8 6 10 11l85 282c2 5 2 10 2 17 7-3 13-7 17-13z m-304 0c-1-3-1-5 0-7 1-1 3-2 6-2l174 0c2 0 4 1 7 2 2 2 4 4 5 7l6 18c0 3 0 5-1 7-1 1-3 2-6 2l-173 0c-3 0-5-1-8-2-2-2-4-4-4-7z m-24-73c-1-3-1-5 0-7 2-2 3-2 6-2l174 0c2 0 5 0 7 2 3 2 4 4 5 7l6 18c1 2 0 5-1 6-1 2-3 3-5 3l-174 0c-3 0-5-1-7-3-3-1-4-4-5-6z"},"click":"function(gd) { \n        // is this being viewed in RStudio?\n        if (location.search == '?viewer_pane=1') {\n          alert('To learn about plotly for collaboration, visit:\\n https://cpsievert.github.io/plotly_book/plot-ly-for-collaboration.html');\n        } else {\n          window.open('https://cpsievert.github.io/plotly_book/plot-ly-for-collaboration.html', '_blank');\n        }\n      }"}],"cloud":false},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1}},"base_url":"https://plot.ly"},"evals":["config.modeBarButtonsToAdd.0.click"],"jsHooks":{"render":[{"code":"function(el, x) { var ctConfig = crosstalk.var('plotlyCrosstalkOpts').set({\"on\":\"plotly_click\",\"persistent\":false,\"dynamic\":false,\"selectize\":false,\"opacityDim\":0.2,\"selected\":{\"opacity\":1}}); }","data":null}]}}</script><!--/html_preserve-->

#### These are the top 10 intervals for the average steps

```r
knitr::kable(activity %>%
    group_by(interval) %>%
    summarise(Mean_steps = mean(steps, na.rm = TRUE)) %>%
    group_by(interval) %>%
    summarise(Average_steps = mean(Mean_steps)) %>%
    arrange(desc(Average_steps)) %>%
    head(10), align = 'l')
```



interval   Average_steps 
---------  --------------
835        206.1698      
840        195.9245      
850        183.3962      
845        179.5660      
830        177.3019      
820        171.1509      
855        167.0189      
815        157.5283      
825        155.3962      
900        143.4528      

### Imputing missing values

#### Code to describe and show a strategy for imputing missing data


```r
## Total number of Rows with missing values
sum(apply(activity, 1, FUN = function(x) {sum(is.na(x))}))
```

```
[1] 2304
```

```r
#### Replace missing values with the mean for the interval ####

##create a merged dataset
new_df <- merge(activity, by_interval, by = "interval")

## substitute values
new_df$steps[is.na(new_df$steps)] <-  new_df$Mean_steps[is.na(new_df$steps)] 

new_df <- new_df %>%
    arrange(date) %>%
    select(steps, date, interval)

new_df$steps <- round(new_df$steps, digits = 0)

## the two datasets are equal but the new_df has no missing data
kable(head(new_df, 10), align = 'l')
```



steps   date         interval 
------  -----------  ---------
2       2012-10-01   0        
0       2012-10-01   5        
0       2012-10-01   10       
0       2012-10-01   15       
0       2012-10-01   20       
2       2012-10-01   25       
1       2012-10-01   30       
1       2012-10-01   35       
0       2012-10-01   40       
1       2012-10-01   45       

```r
kable(head(activity, 10), align = 'l')
```



steps   date         interval 
------  -----------  ---------
NA      2012-10-01   0        
NA      2012-10-01   5        
NA      2012-10-01   10       
NA      2012-10-01   15       
NA      2012-10-01   20       
NA      2012-10-01   25       
NA      2012-10-01   30       
NA      2012-10-01   35       
NA      2012-10-01   40       
NA      2012-10-01   45       

#### Histogram of the total number of steps taken each day after missing values are imputed


```r
by_date_new <- new_df %>%
    group_by(date) %>%
    summarise(N = n(), Total_steps = sum(steps, na.rm = TRUE))

d <- ggplot(by_date_new, aes(x = Total_steps)) + geom_histogram(fill = "#A6CEE3", bins = 30, col = "#1F78B4") +
    ggtitle("Total number of steps Taken each day", subtitle = "No missing data")
ggplotly(d)
```

<!--html_preserve--><div id="cac3960b62f" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="cac3960b62f">{"x":{"data":[{"orientation":"v","width":[729.413793103448,729.413793103448,729.413793103448,729.413793103448,729.413793103448,729.413793103447,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103446,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449,729.413793103449],"base":[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],"x":[0,729.413793103448,1458.8275862069,2188.24137931034,2917.65517241379,3647.06896551724,4376.48275862069,5105.89655172414,5835.31034482759,6564.72413793103,7294.13793103448,8023.55172413793,8752.96551724138,9482.37931034483,10211.7931034483,10941.2068965517,11670.6206896552,12400.0344827586,13129.4482758621,13858.8620689655,14588.275862069,15317.6896551724,16047.1034482759,16776.5172413793,17505.9310344828,18235.3448275862,18964.7586206897,19694.1724137931,20423.5862068966,21153],"y":[2,0,0,1,1,0,1,2,0,1,2,2,3,1,9,12,4,3,6,1,2,5,0,0,1,0,0,0,1,1],"text":["count:  2<br />Total_steps:     0.0000","count:  0<br />Total_steps:   729.4138","count:  0<br />Total_steps:  1458.8276","count:  1<br />Total_steps:  2188.2414","count:  1<br />Total_steps:  2917.6552","count:  0<br />Total_steps:  3647.0690","count:  1<br />Total_steps:  4376.4828","count:  2<br />Total_steps:  5105.8966","count:  0<br />Total_steps:  5835.3103","count:  1<br />Total_steps:  6564.7241","count:  2<br />Total_steps:  7294.1379","count:  2<br />Total_steps:  8023.5517","count:  3<br />Total_steps:  8752.9655","count:  1<br />Total_steps:  9482.3793","count:  9<br />Total_steps: 10211.7931","count: 12<br />Total_steps: 10941.2069","count:  4<br />Total_steps: 11670.6207","count:  3<br />Total_steps: 12400.0345","count:  6<br />Total_steps: 13129.4483","count:  1<br />Total_steps: 13858.8621","count:  2<br />Total_steps: 14588.2759","count:  5<br />Total_steps: 15317.6897","count:  0<br />Total_steps: 16047.1034","count:  0<br />Total_steps: 16776.5172","count:  1<br />Total_steps: 17505.9310","count:  0<br />Total_steps: 18235.3448","count:  0<br />Total_steps: 18964.7586","count:  0<br />Total_steps: 19694.1724","count:  1<br />Total_steps: 20423.5862","count:  1<br />Total_steps: 21153.0000"],"type":"bar","marker":{"autocolorscale":false,"color":"rgba(166,206,227,1)","line":{"width":1.88976377952756,"color":"rgba(31,120,180,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":48.9497716894977},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":"Total number of steps Taken each day","titlefont":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"xaxis":{"domain":[0,1],"type":"linear","autorange":false,"tickmode":"array","range":[-1458.8275862069,22611.8275862069],"ticktext":["0","5000","10000","15000","20000"],"tickvals":[0,5000,10000,15000,20000],"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":"Total_steps","titlefont":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"type":"linear","autorange":false,"tickmode":"array","range":[-0.6,12.6],"ticktext":["0.0","2.5","5.0","7.5","10.0","12.5"],"tickvals":[0,2.5,5,7.5,10,12.5],"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":"count","titlefont":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"barmode":"stack","bargap":0,"hovermode":"closest"},"source":"A","attrs":{"cac7b59a11d":{"x":{},"type":"ggplotly"}},"cur_data":"cac7b59a11d","visdat":{"cac7b59a11d":["function (y) ","x"]},"config":{"modeBarButtonsToAdd":[{"name":"Collaborate","icon":{"width":1000,"ascent":500,"descent":-50,"path":"M487 375c7-10 9-23 5-36l-79-259c-3-12-11-23-22-31-11-8-22-12-35-12l-263 0c-15 0-29 5-43 15-13 10-23 23-28 37-5 13-5 25-1 37 0 0 0 3 1 7 1 5 1 8 1 11 0 2 0 4-1 6 0 3-1 5-1 6 1 2 2 4 3 6 1 2 2 4 4 6 2 3 4 5 5 7 5 7 9 16 13 26 4 10 7 19 9 26 0 2 0 5 0 9-1 4-1 6 0 8 0 2 2 5 4 8 3 3 5 5 5 7 4 6 8 15 12 26 4 11 7 19 7 26 1 1 0 4 0 9-1 4-1 7 0 8 1 2 3 5 6 8 4 4 6 6 6 7 4 5 8 13 13 24 4 11 7 20 7 28 1 1 0 4 0 7-1 3-1 6-1 7 0 2 1 4 3 6 1 1 3 4 5 6 2 3 3 5 5 6 1 2 3 5 4 9 2 3 3 7 5 10 1 3 2 6 4 10 2 4 4 7 6 9 2 3 4 5 7 7 3 2 7 3 11 3 3 0 8 0 13-1l0-1c7 2 12 2 14 2l218 0c14 0 25-5 32-16 8-10 10-23 6-37l-79-259c-7-22-13-37-20-43-7-7-19-10-37-10l-248 0c-5 0-9-2-11-5-2-3-2-7 0-12 4-13 18-20 41-20l264 0c5 0 10 2 16 5 5 3 8 6 10 11l85 282c2 5 2 10 2 17 7-3 13-7 17-13z m-304 0c-1-3-1-5 0-7 1-1 3-2 6-2l174 0c2 0 4 1 7 2 2 2 4 4 5 7l6 18c0 3 0 5-1 7-1 1-3 2-6 2l-173 0c-3 0-5-1-8-2-2-2-4-4-4-7z m-24-73c-1-3-1-5 0-7 2-2 3-2 6-2l174 0c2 0 5 0 7 2 3 2 4 4 5 7l6 18c1 2 0 5-1 6-1 2-3 3-5 3l-174 0c-3 0-5-1-7-3-3-1-4-4-5-6z"},"click":"function(gd) { \n        // is this being viewed in RStudio?\n        if (location.search == '?viewer_pane=1') {\n          alert('To learn about plotly for collaboration, visit:\\n https://cpsievert.github.io/plotly_book/plot-ly-for-collaboration.html');\n        } else {\n          window.open('https://cpsievert.github.io/plotly_book/plot-ly-for-collaboration.html', '_blank');\n        }\n      }"}],"cloud":false},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1}},"base_url":"https://plot.ly"},"evals":["config.modeBarButtonsToAdd.0.click"],"jsHooks":{"render":[{"code":"function(el, x) { var ctConfig = crosstalk.var('plotlyCrosstalkOpts').set({\"on\":\"plotly_click\",\"persistent\":false,\"dynamic\":false,\"selectize\":false,\"opacityDim\":0.2,\"selected\":{\"opacity\":1}}); }","data":null}]}}</script><!--/html_preserve-->

```r
steps_summary_new <- by_date_new %>%
    summarise(Mean_steps = mean(Total_steps, na.rm = TRUE),
              Median_steps = median(Total_steps, na.rm = TRUE))

kable(steps_summary_new, align = 'l')
```



Mean_steps   Median_steps 
-----------  -------------
10765.64     10762        

Mean and Median are not the same. They have become higher, as expected.

### Are there differences in activity patterns between weekdays and weekends?


```r
new_df$Weekday <- weekdays(new_df$date)
new_df$Week_part <- ifelse(new_df$Weekday %in% c("Sabato", "Domenica"), "Weekend", "Weekday")
head(new_df)
```

```
  steps       date interval Weekday Week_part
1     2 2012-10-01        0  Lunedì   Weekday
2     0 2012-10-01        5  Lunedì   Weekday
3     0 2012-10-01       10  Lunedì   Weekday
4     0 2012-10-01       15  Lunedì   Weekday
5     0 2012-10-01       20  Lunedì   Weekday
6     2 2012-10-01       25  Lunedì   Weekday
```

#### Panel plot comparing the average number of steps taken per 5-minute interval across weekdays and weekends


```r
n = new_df %>%
    group_by(interval, Week_part) %>%
    summarise(mean_score = mean(steps))

ggplot(n, aes(x = interval, y = mean_score)) + geom_path() +
    facet_wrap(~Week_part, nrow = 2) + ylab("Number of Steps") +
    theme_light()
```

![](PA1_template_files/figure-html/unnamed-chunk-9-1.png)<!-- -->

