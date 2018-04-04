---
##Title: "R Markdown Assignment"
#author: "Khiem Nguyen"
output: html_document
This is Khiem Nguyen R Markdown Assignment for Next Generation Sequences Class, the second week.

Seed of wildtype and 6 chlorophyl deficiency mutant rice were received from Japan. Plants were grown in a vermiculite -soil mixture un controlled-environtment chamber at 60% RH, 12 hours period, and a photosynthetic photon flux desity approximately 250-500 micromol m-2 sec-1. Temperature was 25 degree
The Chl content of  6 chlorophyl deficiency mutant strains of wildtype rice.
```{r, echo = FALSE}
chl1 <- c(2156.28, 2234.05, 2134.12)
chl2 <- c(1693.42, 1572.43, 1467.23)
chl3 <- c(2644.67, 2265.14, 2425.29)
chl4 <- c(2502.48, 2455.32, 2555.12)
chl5 <- c(2477.20, 2344.6, 2017.75)
chl6 <- c(2044.6, 2217.75, 2121.14)
wt <- c(3705.24, 3622.42, 3857.24)
chlcontent <- data.frame(chl1, chl2, chl3, chl4, chl5, chl6, wt)
summary(chlcontent)
```

The Chla and Chlb content of 6 chlorophyl deficiency mutant strains of wildtype rice.
```{r, echo = FALSE}
chla1 <- c(8.2, 7.9, 8.1)
chlb1 <- c(0.2, 0.16, 0.19)
chla2 <- c(6.5, 6.3, 6.7)
chlb2 <- c(0.12, 0.29, 0.14)
chla3 <- c(14.8, 14.3,13.5)
chlb3 <- c(0.21, 0.17, 0.19)
chla4 <- c(14.3, 13.87, 14.2)
chlb4 <- c(0.06, 0.05, 0.09)
chla5 <- c(11.4, 12.01, 11.8)
chlb5 <- c(0.02, 0.03, 0.06)
chla6 <- c(28.7, 25.5, 26.5)
chlb6 <- c(0.03, 0.04, 0.07)
wta <- c(19.6, 18.7, 19.7)
wtb <- c(5.13, 6.06, 6.54)
chla<- data.frame (chla1, chla2, chla3, chla4, chla5, chla6, wta)
chlb<- data.frame (chlb1, chlb2, chlb3, chlb4, chlb5, chlb6, wtb)
summary(chla)
summary(chlb)
```

**Table 1: Total Chl, Chla, Chlb content and ratio of Chla/b of 6 chlorophyll deficiency strain and wildtype rice**

Strain  |**Chl content (mg/ml)**|**Chla(g/ml)**|**Chlb (g/ml)**|**Chla/b**
--------|-------------------|------------------|---------------|-----------
chl1    |   2175            |       8.067      |     0.1833    |  44.34
chl2    |   1578            |       6.5        |     0.1833    |  41.25
chl3    |   2445            |       14.20      |     0.19      |  75.22
chl4    |   2504            |       14.12      |     0.066     |  224.5
chl5    |   2280            |       11.74      |     0.036     |  389.0
chl6    |   2128            |       26.9       |     0.04      |  657.6
wt      |   3728            |       19.33      |     5.91      |  3.306
  
  
```{r, echo = FALSE}
chla.b <- chla/chlb
CHLCONTENT <- c(2175, 1578, 2445, 2504, 2280, 2128, 3728)
CHLA <- c(8.057, 6.5, 14.20, 14.12, 11.74, 26.9, 19.33)
CHLB <- c(0.1833, 0.1833, 0.19, 0.066, 0.036, 0.04, 5.91)
CHLA.B <-c(44.34 , 41.25 , 75.22 , 225.5 ,389 , 657.6 , 3.306)
strain<- c("c1","c2","c3","c4","c5","c6","wt")
rice <- data.frame (CHLCONTENT, CHLA, CHLB, CHLA.B, strain)
```

#*PLOT*
```{r, echo = FALSE}
plot(rice)
```

```{r, echo = FALSE, included = FALSE}
library(plotly)
plot_ly(rice, x = ~strain, y = ~CHLCONTENT ,name = "Chl content and mutant strain",type = "bar",marker = list(color = 'rgb(158,202,225)', line = list(color = 'rgb(8,48,107)', width = 1.5)))
```
#*Fig 1* Chl content of wildtype and chlorophyll deficiency mutant strain of rice*

```{r, echo = FALSE, included = FALSE}
library(plotly)
plot_ly(rice, x = ~strain, y = ~CHLA.B ,name = "Chl content and mutant strain",type = "bar",marker = list(color = 'rgb(158,202,225)', line = list(color = 'rgb(8,48,107)', width = 1.5)))
```
#*Fig 2* Ratio of Chla/b content of wildtype and chlorophyll deficiency mutant strain of rice*


#Rice boxplot
```{r, echo = FALSE}
boxclo <- c(2156.28, 2234.05, 2134.12,1693.42, 1572.43, 1467.23,2644.67, 2265.14, 2425.29,2502.48, 2455.32, 2555.12,2477.20, 2344.6, 2017.75,2044.6, 2217.75, 2121.14,3705.24, 3622.42, 3857.24)
boxstrain <-c("c1","c1","c1","c2","c2","c2","c3","c3","c3","c4","c4","c4","c5","c5","c5","c6","c6","c6","wt","wt","wt")
boxrice <- data.frame(boxclo, boxstrain)
box <- ggplot(boxrice, aes(x=boxstrain, y=boxclo))
box + geom_boxplot(aes(fill=boxclo)) + 
  ylab("chlorophyll content") + ggtitle("Rice Boxplot") +
  stat_summary(fun.y=mean, geom="point", shape=5, size=4) 
```

##Scatter Plot
```{r, echo=FALSE}
boxchla <- c(8.2, 7.9, 8.1,6.5, 6.3, 6.7,14.8, 14.3,13.5,14.3, 13.87, 14.2,11.4, 12.01, 11.8,28.7, 25.5, 26.5, 19.6, 18.7, 19.7)
boxchlb <- c(0.2, 0.16, 0.19,0.12, 0.29, 0.14,0.21, 0.17, 0.19, 0.06, 0.05, 0.09, 0.02, 0.03, 0.06, 0.03, 0.04, 0.07, 5.13, 6.06, 6.54)
boxchla.b <-boxchla/boxchlb
boxrice1 <- data.frame (boxclo, boxchla.b, boxstrain)
smooth <- ggplot(boxrice1, aes(x=boxclo, y=boxchla.b, color=boxstrain)) + 
  geom_point(aes(shape=boxstrain), size=1.5) + xlab("Chlorophyll content") + ylab("Ratio a/b") + 
  ggtitle("Scatterplot with smoothers")

# Linear model
smooth + geom_smooth(method="lm")
```
After 4 weeks of growth the appearance of mature leaves of the wildtype and chlorophyll deficiency mutant rice, all mutants contain less Chl than wildtype. The ratio of Chl content higher than wildtype specific is c6. Data indicated that mutant was reduced photosyntheis ability compared to wildtype.
