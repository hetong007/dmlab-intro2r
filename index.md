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
##   [1]  8.4148  1.4115  1.9166  2.6576  6.7905  3.0909  7.1984  8.4458
##   [9]  3.2309  8.1880 -0.3137  5.6411  3.4896  6.7891  4.4245  6.4768
##  [17]  1.6799  7.8890  4.8355  7.5728  4.7980 -0.5749  4.3500  6.5675
##  [25]  3.9754  6.5211  6.2522  6.6849  2.2563  7.1407  5.0972  6.5552
##  [33]  6.0741  1.3744  8.1244  6.4716  1.1548  3.2167  6.7187 -1.9521
##  [41]  6.3465  2.5288  2.2566  4.4020  5.9173  2.7768  5.5261  4.7015
##  [49]  4.9731  0.3502  6.6587  2.8315 -0.4497  0.5091  7.0458  2.5252
##  [57]  7.8604  5.1703  7.8117  3.3512  6.0971  8.3217  3.5075  7.2513
##  [65]  1.8094  4.8007  3.5442  4.4679  3.5365 -0.9916  3.6653  2.3381
##  [73]  4.4729  5.1480  7.6398  4.0272  3.0952  3.9126  4.0050 11.1871
##  [81]  7.3031  2.9386  3.0635  0.8264  5.7611  5.9373  4.5907 10.2018
##  [89]  5.6733 -1.7092  3.3747  4.5797  6.6282  3.7543  7.7073  8.3110
##  [97]  4.0444  6.4197  0.1034  2.7448
```

```r
groupB
```

```
##  [1] 12.428  8.289  7.646 11.278 12.031  4.606 10.267 13.370  9.326 10.461
## [11]  6.147 11.619  6.478  7.978 10.613 11.879 13.692  7.821  5.049 12.639
## [21]  9.025  9.690  6.937 11.604 13.090
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
## t = -8.708, df = 36.84, p-value = 8.978e-11
## alternative hypothesis: true difference in means is less than 0
## 95 percent confidence interval:
##    -Inf -4.177
## sample estimates:
## mean of x mean of y 
##     4.578     9.758
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
##     -0.0424       4.9804
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
## -2.1616 -0.6396 -0.0066  0.5037  2.2849 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)  -0.0424     0.0961   -0.44     0.66    
## x             4.9804     0.0931   53.49   <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 0.959 on 98 degrees of freedom
## Multiple R-squared:  0.967,	Adjusted R-squared:  0.967 
## F-statistic: 2.86e+03 on 1 and 98 DF,  p-value: <2e-16
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
##   0.004   0.000   0.004
```

```r
system.time({
  for (i in 1:length(a))
    a[i]+b[i]
})
```

```
##    user  system elapsed 
##   0.957   0.005   0.964
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
## [1] -0.7524  0.8390 -0.3736  0.2736 -0.2715 -0.8221
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



<link rel='stylesheet' href=/grad/3/hetongh/R/x86_64-unknown-linux-gnu-library/3.0/rCharts/libraries/nvd3/css/nv.d3.css>
<link rel='stylesheet' href=/grad/3/hetongh/R/x86_64-unknown-linux-gnu-library/3.0/rCharts/libraries/nvd3/css/rNVD3.css>
<script type='text/javascript' src=/grad/3/hetongh/R/x86_64-unknown-linux-gnu-library/3.0/rCharts/libraries/nvd3/js/jquery-1.8.2.min.js></script>
<script type='text/javascript' src=/grad/3/hetongh/R/x86_64-unknown-linux-gnu-library/3.0/rCharts/libraries/nvd3/js/d3.v3.min.js></script>
<script type='text/javascript' src=/grad/3/hetongh/R/x86_64-unknown-linux-gnu-library/3.0/rCharts/libraries/nvd3/js/nv.d3.min-new.js></script>
<script type='text/javascript' src=/grad/3/hetongh/R/x86_64-unknown-linux-gnu-library/3.0/rCharts/libraries/nvd3/js/fisheye.js></script> 
 <style>
  .rChart {
    display: block;
    margin-left: auto; 
    margin-right: auto;
    width: 800px;
    height: 500px;
  }  
  </style>
<div id = 'chart71ba1024b750' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawchart71ba1024b750()
    });
    function drawchart71ba1024b750(){  
      var opts = {
 "dom": "chart71ba1024b750",
"width":    800,
"height":    500,
"x": "Hair",
"y": "Freq",
"group": "Eye",
"type": "multiBarChart",
"id": "chart71ba1024b750" 
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

<iframe src=' assets/fig/unnamed-chunk-19.html ' scrolling='no' frameBorder='0' seamless class='rChart morris ' id=iframe- chart71ba6e5de8c5 ></iframe> <style>iframe.rChart{ width: 100%; height: 400px;}</style>

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











































