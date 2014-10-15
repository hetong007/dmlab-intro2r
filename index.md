---
title       : Introduction to R
subtitle    : with unique features
author      : Tong He
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
ext_widgets : {rCharts: [libraries/nvd3]}
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
##   [1]  3.5794  6.3882  6.8609  5.3853  1.1379  8.7237  3.6871  3.5696
##   [9] 10.9958  6.1629  6.7984 12.2326  4.4837  1.3916  3.1010  1.2401
##  [17]  6.0099  4.9802  3.0352  1.3786  3.7145  3.4193 -0.6099  2.3239
##  [25]  8.4922 -2.6229  7.3236  8.7738  4.3974  5.4352  5.9593 11.5257
##  [33]  3.8268  2.6914  7.9993  3.9392  1.3178 10.9439  2.4811  4.1416
##  [41]  1.7222  5.3926  2.0505  7.8467  2.2538  9.9531  7.4375  5.3570
##  [49]  8.3734  4.8220  7.4037  0.4452  0.6344  4.4650  7.2380  4.1444
##  [57]  5.0855 -0.5332  5.2301  8.7919 13.6589  0.5906  4.7456  9.2781
##  [65]  8.2843  2.4842  5.3055  5.7935  2.7734  2.1242  3.7565  6.3098
##  [73]  7.8208  5.3100 11.3600  8.3838  9.2205  7.7164  5.8169  3.5496
##  [81]  3.3919  3.4113  8.4184  3.9099  6.2352  6.3927  9.4745 -2.2387
##  [89]  7.0482  4.8425  8.8880 10.2136  6.1407  7.1922  3.5413  3.0456
##  [97]  5.5005 -1.0879  2.2165  5.7653
```

```r
groupB
```

```
##  [1] 10.192  7.723  7.410 11.962 12.419  6.689  8.946 15.626 11.142 10.538
## [11]  2.476 14.820 11.435  5.950 11.482 10.093  9.029  6.298 10.159  7.088
## [21] 10.615 15.246  8.844  0.967  4.448
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
## t = -5.081, df = 34.05, p-value = 6.726e-06
## alternative hypothesis: true difference in means is less than 0
## 95 percent confidence interval:
##    -Inf -2.703
## sample estimates:
## mean of x mean of y 
##     5.213     9.264
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
##       0.154        4.965
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
## -3.1337 -0.7504 -0.0153  0.7365  2.1416 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)   0.1543     0.0978    1.58     0.12    
## x             4.9653     0.1023   48.51   <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 0.977 on 98 degrees of freedom
## Multiple R-squared:  0.96,	Adjusted R-squared:  0.96 
## F-statistic: 2.35e+03 on 1 and 98 DF,  p-value: <2e-16
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
##   0.005   0.000   0.004
```

```r
system.time({
  for (i in 1:length(a))
    a[i]+b[i]
})
```

```
##    user  system elapsed 
##   0.928   0.003   0.932
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
## [1]  0.9888  1.0628  0.2080  1.3649 -2.4064  1.2872
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




<div id = 'chart71ba3611c709' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawchart71ba3611c709()
    });
    function drawchart71ba3611c709(){  
      var opts = {
 "dom": "chart71ba3611c709",
"width":    800,
"height":    500,
"x": "Hair",
"y": "Freq",
"group": "Eye",
"type": "multiBarChart",
"id": "chart71ba3611c709" 
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











































