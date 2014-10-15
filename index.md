---
title       : Introduction to R
subtitle    : with unique features
author      : Tong He
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [nvd3,morris]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Outline

- R: Born for statistics.
- Thousands of packages for data analysis
- Reproducible report
    - knitr
    - slidify
    - rmarkdown
- Data Visualization
    - ggplot2
    - rCharts
- Web application
    - shiny

--- .segue .dark

## The GNU-R project

---

## R: Born for statistics

History:

- From the S language, which is inspired by Scheme.
- Created by [Ross Ihaka](http://en.wikipedia.org/wiki/Ross_Ihaka) and [Robert Gentleman](http://en.wikipedia.org/wiki/Robert_Gentleman_%28statistician%29).

---

## R: Born for statistics

R is strong for statistical missions. 

- Strong matrix calculation ability
- Native support for statistics
- Abundant third-party packages

---

## R: Born for statistics


```r
groupA = rnorm(100,5,3)
groupB = rnorm(25,10,3)
groupA
```

```
##   [1]  8.7247  4.5361  0.3788 -0.8695  3.2872  3.4701  2.8546  3.5315
##   [9]  6.1452  9.4967  8.5841  1.4677  7.4127  5.6425  5.8835  5.5284
##  [17]  5.0099  6.0896  9.3668  2.2322  2.5924 -0.4686  7.6782  3.4858
##  [25]  3.1851  4.5650  4.8263  1.9470  6.2423  3.5898  3.6703  5.9814
##  [33]  2.3010  6.8946  1.0961  5.9623  0.1530  3.9873  7.7199  4.4135
##  [41]  8.6039  0.7672 10.6175  7.3712  7.9363 10.1943  3.7506  4.0459
##  [49] -3.7036  5.0571  5.7533  4.6721  6.7473  1.5737  0.1261 10.4451
##  [57]  9.0248 -0.1060  3.9819  1.2864  4.0724 11.1422  3.7656  7.5389
##  [65] -0.9361  0.3266  3.8153  2.3117  2.5620  5.3630  2.7921  7.3520
##  [73]  3.1333  5.8310  3.8323  8.3736  5.2174  5.0827  6.6860  4.7006
##  [81]  5.0347  7.1327  9.4149  7.0446  5.8658  8.3377  3.1650  4.3835
##  [89] -0.8057  3.4256 10.7067  1.0343  7.8309  5.4453  9.1047  4.5595
##  [97]  6.3318 11.8561  3.5041  8.1146
```

```r
groupB
```

```
##  [1]  7.402  7.090 11.660  7.991  9.747  8.846  8.614  8.422 12.317  9.130
## [11] 10.138  9.953  8.440  9.002 11.019 10.991 11.115  8.688  9.193  8.710
## [21]  9.577  5.530  7.097  7.974  5.888
```

---

## R: Born for statistics


```r
t.test(groupA,groupB,alternative = c("less"))
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  groupA and groupB
## t = -8.866, df = 69.85, p-value = 2.365e-13
## alternative hypothesis: true difference in means is less than 0
## 95 percent confidence interval:
##    -Inf -3.304
## sample estimates:
## mean of x mean of y 
##     4.912     8.981
```

---

## R: Born for statistics


```r
x = rnorm(100)
y = 5*x+rnorm(100,0,1)
lm.model = lm(y~x)
lm.model
```

```
## 
## Call:
## lm(formula = y ~ x)
## 
## Coefficients:
## (Intercept)            x  
##       -0.06         4.96
```

---

## R: Born for statistics


```r
summary(lm.model)
```

```
## 
## Call:
## lm(formula = y ~ x)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -2.0235 -0.7848 -0.0118  0.6506  2.4621 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)  -0.0600     0.0987   -0.61     0.55    
## x             4.9557     0.0980   50.55   <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 0.987 on 98 degrees of freedom
## Multiple R-squared:  0.963,	Adjusted R-squared:  0.963 
## F-statistic: 2.55e+03 on 1 and 98 DF,  p-value: <2e-16
```

---

## R: Born for statisitics


```r
plot(x,y,pch=20)
abline(lm.model,col=2)
```

<img src="assets/fig/unnamed-chunk-5.png" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" style="display: block; margin: auto;" />

---

## Third party packages

- [CRAN](http://www.r-project.org/)(The Comprehensive R Archive Network) is managing over 5,000 R packages.
    - Strict quality control
    - [Task Views](http://cran.r-project.org/web/views/)
    - My package [xgboost](http://cran.r-project.org/web/packages/xgboost/index.html)
- [R-Forge](https://r-forge.r-project.org/) is an SVN repository for packages.
- [Bioconductor](http://www.bioconductor.org/) focus on biostat and bioinfo packages.
- [Github](http://github.com) more flexible.

---

## Third party packages

To install a package, say `xgboost`, on CRAN, just type 


```r
install.packages('xgboost')
```

To install `xgboost` from github, we need 


```r
require(devtools)
install_github('xgboost','tqchen',subdir='R-package')
```

--- &twocol

## The community and environment

*** =left

The community

- Mailing lists
- Stackoverflow / Cross Validation
- R conference

*** =right

The environment

- IDE: RStudio
  - Server version for collaboration
  - Many fancy stuffs later
- Commercial version
  - Revolution

--- .segue .dark

## Unique features in R

---

## Vectorization


```r
a = 1:1000000
b = 1:1000000
system.time({a+b})
```

```
##    user  system elapsed 
##   0.032   0.001   0.033
```

```r
system.time({
  for (i in 1:length(a))
    a[i]+b[i]
})
```

```
##    user  system elapsed 
##   0.964   0.007   0.973
```

Let C to do loop.

---

## Vectorization

R is also strong in (sparse) matrix computation.


```r
library('Matrix')
 
m1 = matrix(0, nrow = 1000, ncol = 1000)
m2 = Matrix(0, nrow = 1000, ncol = 1000, sparse = TRUE)
 
object.size(m1)
```

```
## 8000200 bytes
```

```r
object.size(m2)
```

```
## 5632 bytes
```

---

## Vectorization


```r
m1[500, 500] <- 1
m2[500, 500] <- 1
 
object.size(m1)
```

```
## 8000200 bytes
```

```r
object.size(m2)
```

```
## 5648 bytes
```

---

## Vectorization


```r
m2 %*% rnorm(1000)
m2 + m2
m2 - m2
t(m2)
```

---

## Vectorization

R can also take advantage from the parallelization of *BLAS libraries. There are several choices:

- OpenBLAS
- ATLAS
- HiPLAR

[Here](http://www.stat.cmu.edu/~nmv/2013/07/09/for-faster-r-use-openblas-instead-better-than-atlas-trivial-to-switch-to-on-ubuntu/)'s a tutorial for apt-get style installation on Ubuntu.

---

## Reproducible Report

Insert code and result in a slide is painful.

- Copy & paste
- Formatting
- Update code and report seperately

---

## Reproducible Report


```r
rnums = rnorm(10000)
head(rnums)
```

```
## [1]  1.0507  0.3592 -0.1029  1.0026  1.5919  0.3095
```

```r
hist(rnums,breaks=50)
```

<img src="assets/fig/unnamed-chunk-12.png" title="plot of chunk unnamed-chunk-12" alt="plot of chunk unnamed-chunk-12" style="display: block; margin: auto;" />

---

## Reproducible Report

This is supported by the package [`knitr`](http://yihui.name/knitr/):

- Markdown-based grammar with HTML codes as extension
- Webpage based output

We'll see the 'Webpage based output' is important.

--- &twocol

## Reproducible Report

This slide is produced by the package [`slidify`](https://github.com/ramnathv/slidify).

- Based on `knitr`
- Abundant templates
- Easy to share

---

## Reproducible Report

Now I write all the assignments with `rmarkdown`:

- Based on `knitr`
- Allowing formatting and templates
- Using `pandoc` as the backend
    - PDF
    - HTML
    - Word(yes, even word)

--- &twocol

## Data Visualization

Data visualization is sometimes important. Compare these two graphs:

*** =left

![plot of chunk unnamed-chunk-13](assets/fig/unnamed-chunk-13.png) 

*** =right

![plot of chunk unnamed-chunk-14](assets/fig/unnamed-chunk-14.png) 

--- &twocol

## Data Visualization

Or we can have other variations:

*** =left

![plot of chunk unnamed-chunk-15](assets/fig/unnamed-chunk-15.png) 

*** =right

![plot of chunk unnamed-chunk-16](assets/fig/unnamed-chunk-16.png) 

---

## Data Visualization

Sometimes static pictures are not enough:



<link rel='stylesheet' href=//cdnjs.cloudflare.com/ajax/libs/nvd3/1.1.15-beta/nv.d3.min.css>
<script type='text/javascript' src=//ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js></script>
<script type='text/javascript' src=//d3js.org/d3.v3.min.js></script>
<script type='text/javascript' src=//cdnjs.cloudflare.com/ajax/libs/nvd3/1.1.15-beta/nv.d3.min.js></script>
<script type='text/javascript' src=//nvd3.org/assets/lib/fisheye.js></script> 
 <style>
  .rChart {
    display: block;
    margin-left: auto; 
    margin-right: auto;
    width: 800px;
    height: 500px;
  }  
  </style>
<div id = 'chart71ba31f3792a' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawchart71ba31f3792a()
    });
    function drawchart71ba31f3792a(){  
      var opts = {
 "dom": "chart71ba31f3792a",
"width":    800,
"height":    500,
"x": "Hair",
"y": "Freq",
"group": "Eye",
"type": "multiBarChart",
"id": "chart71ba31f3792a" 
},
        data = [
 {
 "Hair": "Black",
"Eye": "Brown",
"Sex": "Male",
"Freq":             32 
},
{
 "Hair": "Brown",
"Eye": "Brown",
"Sex": "Male",
"Freq":             53 
},
{
 "Hair": "Red",
"Eye": "Brown",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Blond",
"Eye": "Brown",
"Sex": "Male",
"Freq":              3 
},
{
 "Hair": "Black",
"Eye": "Blue",
"Sex": "Male",
"Freq":             11 
},
{
 "Hair": "Brown",
"Eye": "Blue",
"Sex": "Male",
"Freq":             50 
},
{
 "Hair": "Red",
"Eye": "Blue",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Blond",
"Eye": "Blue",
"Sex": "Male",
"Freq":             30 
},
{
 "Hair": "Black",
"Eye": "Hazel",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Brown",
"Eye": "Hazel",
"Sex": "Male",
"Freq":             25 
},
{
 "Hair": "Red",
"Eye": "Hazel",
"Sex": "Male",
"Freq":              7 
},
{
 "Hair": "Blond",
"Eye": "Hazel",
"Sex": "Male",
"Freq":              5 
},
{
 "Hair": "Black",
"Eye": "Green",
"Sex": "Male",
"Freq":              3 
},
{
 "Hair": "Brown",
"Eye": "Green",
"Sex": "Male",
"Freq":             15 
},
{
 "Hair": "Red",
"Eye": "Green",
"Sex": "Male",
"Freq":              7 
},
{
 "Hair": "Blond",
"Eye": "Green",
"Sex": "Male",
"Freq":              8 
} 
]
  
      if(!(opts.type==="pieChart" || opts.type==="sparklinePlus" || opts.type==="bulletChart")) {
        var data = d3.nest()
          .key(function(d){
            //return opts.group === undefined ? 'main' : d[opts.group]
            //instead of main would think a better default is opts.x
            return opts.group === undefined ? opts.y : d[opts.group];
          })
          .entries(data);
      }
      
      if (opts.disabled != undefined){
        data.map(function(d, i){
          d.disabled = opts.disabled[i]
        })
      }
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .width(opts.width)
          .height(opts.height)
          
        if (opts.type != "bulletChart"){
          chart
            .x(function(d) { return d[opts.x] })
            .y(function(d) { return d[opts.y] })
        }
          
         
        
          
        

        
        
        
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>

---

## Data Visualization


```
## Loading required package: reshape2
```

<iframe src=' assets/fig/unnamed-chunk-19.html ' scrolling='no' frameBorder='0' seamless class='rChart morris ' id=iframe- chart71baa36d4f0 ></iframe> <style>iframe.rChart{ width: 100%; height: 400px;}</style>

--- .segue .dark

## Web Application

---

## Web Application

Integrate all the previous features, we can merge them into a web app.

Yes, we can build a web app in R!

---

## Web Application

Examples: 

1. [Kmeans on iris data](http://shiny.rstudio.com/gallery/kmeans-example.html)
2. [Combining rCharts](http://shiny.rstudio.com/gallery/nvd3-line-chart-output.html)
3. [Wordcloud](http://shiny.rstudio.com/gallery/word-cloud.html)

---

## Web Application

Advanced Examples:

1. [imgSVD](https://hetong.shinyapps.io/imgsvd)
2. [Chat Room](http://shiny.rstudio.com/gallery/chat-room.html)
3. [Downloadable report genereation](http://shiny.rstudio.com/gallery/download-knitr-reports.html)
4. [Dynamic Clustering](http://shiny.rstudio.com/gallery/dynamic-clustering.html)
5. [Multi-language-character encoding](http://shiny.rstudio.com/gallery/unicode-characters.html)
6. [Personalization and authencation](http://shiny.rstudio.com/gallery/personalized-ui.html)

Enjoy more from the [gallery](http://shiny.rstudio.com/gallery/).

---

## Summarize

One of the important feature is the 'Webpage based output'. 

Tools as 

- ggplot2/rCharts
- knitr/slidify/rmarkdown
- shiny

enable us directly share R code and trustful result around the world.

--- &twocol

## Why does R need them

Why these are features unique?

*** =left

Academical application:

- Teaching
- Research

Demonstrate the numbers and graphs from the computation is important. And the need for sharing and publishing a report/lecture/tutorial is increasing.

*** =right

Industrial application:

- Internal communication
- Business report
- Automatic report generation

R is mostly used with data related missions. Usually clients would like to get information from slides with beautiful pictures. The report system connects the demonstration and data manipulation.

--- .segue .dark

## FAQ











































