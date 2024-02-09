# Naumi-Rasha-HW2
HW2
NAUMI RASHA
2024-02-09
R Markdown
This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see http://rmarkdown.rstudio.com.

When you click the Knit button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

summary(cars)
##      speed           dist       
##  Min.   : 4.0   Min.   :  2.00  
##  1st Qu.:12.0   1st Qu.: 26.00  
##  Median :15.0   Median : 36.00  
##  Mean   :15.4   Mean   : 42.98  
##  3rd Qu.:19.0   3rd Qu.: 56.00  
##  Max.   :25.0   Max.   :120.00
load("~/Documents/brfss22/BRFSS2022/BRFSS2022_rev.RData")
library(tidyverse)
## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
## ✔ dplyr     1.1.4     ✔ readr     2.1.5
## ✔ forcats   1.0.0     ✔ stringr   1.5.1
## ✔ ggplot2   3.4.4     ✔ tibble    3.2.1
## ✔ lubridate 1.9.3     ✔ tidyr     1.3.1
## ✔ purrr     1.0.2     
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
library(ggplot2)
I worked with Chamiqua and Allegra.

xtabs(~ brfss22$ADDEPEV3 + brfss22$SEXVAR)
##                                        brfss22$SEXVAR
## brfss22$ADDEPEV3                          Male Female
##   Yes ever told had depressive disorder  31096  60314
##   No                                    176718 174192
prop.table(table(brfss22$ADDEPEV3, brfss22$SEXVAR))
##                                        
##                                               Male     Female
##   Yes ever told had depressive disorder 0.07030204 0.13635829
##   No                                    0.39952523 0.39381443
NN <- length(brfss22$ADDEPEV3)
set.seed(12345)
restrict_1 <- (runif(NN) < 0.1) # use just 10% 
summary(restrict_1)
##    Mode   FALSE    TRUE 
## logical  400624   44508
brfss_small <- subset(brfss22, restrict_1)
ggplot(brfss_small, aes(x = INCOME3, fill = ADDEPEV3)) + geom_bar()


ggplot(brfss_small, aes(x = ADDEPEV3, fill = INCOME3)) + geom_bar()


ggplot(brfss_small, aes(x = INCOME3, fill = ADDEPEV3)) + geom_bar(position = "fill")


ggplot(brfss_small, aes(x = ADDEPEV3, fill = INCOME3)) + geom_bar(position = "fill")
 I found this data interesting because I could see how income plays a big part in depression, many people with more income show that they have depression, but the reason behind this could be being able to afford to get help.
