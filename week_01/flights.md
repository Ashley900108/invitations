---
title: "Flights"
format: html
editor: visual
date: "April 22, 2023"
execute:
  keep-md: true
  format:
  html:
    code-fold: true
    code-line-numbers: true
---


::: {.cell Warning='false' Message='false'}

```{.r .cell-code}
library(tidyverse)
```

::: {.cell-output .cell-output-stderr}
```
── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
✔ dplyr     1.1.1     ✔ readr     2.1.4
✔ forcats   1.0.0     ✔ stringr   1.5.0
✔ ggplot2   3.4.2     ✔ tibble    3.2.1
✔ lubridate 1.9.2     ✔ tidyr     1.3.0
✔ purrr     1.0.1     
── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```
:::

```{.r .cell-code}
library(nycflights13)
library(ggplot2)
library(pander)
library(DT)
```
:::


## Summary

I chose the Flight Carrier and the Delay Arrival Time as the topic of this assignment. I personally have experienced some plane delays and know the painfulness of having to stay in the airport for a longer time than expected. Therefore, I thought knowing the flight carrier that avoid the arrival delay well can be helpful for every person who travel with air planes.


::: {.cell}

```{.r .cell-code}
fl1<-flights%>%select(c(carrier,arr_delay))%>%filter(arr_delay!="NA")
```
:::


## First Variable -- Carrier


::: {.cell}

```{.r .cell-code}
table(fl1$carrier)%>%pander
```

::: {.cell-output-display}
-----------------------------------------------------------------------------
  9E      AA     AS     B6      DL      EV     F9     FL    HA     MQ     OO 
------- ------- ----- ------- ------- ------- ----- ------ ----- ------- ----
 17294   31947   709   54049   47658   51108   681   3175   342   25037   29 
-----------------------------------------------------------------------------

Table: Table continues below

 
------------------------------------
  UA      US      VX     WN     YV  
------- ------- ------ ------- -----
 57782   19831   5116   12044   544 
------------------------------------
:::
:::


## Second Variable -- Arrival Delay Time (min) {.tabset}

### Hide

### Show


::: {.cell Warning='false'}

```{.r .cell-code}
fl3<-fl1%>%select(arr_delay)
datatable(fl3)
```

::: {.cell-output .cell-output-stderr}
```
Warning in instance$preRenderHook(instance): It seems your data is too big for
client-side DataTables. You may consider server-side processing:
https://rstudio.github.io/DT/server.html
```
:::

::: {.cell-output-display}

```{=html}
<div class="datatables html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-dafd991ae48962bff326" style="width:100%;height:auto;"></div>
```

:::
:::

##

## Combination of the Two Variables

::: {.cell}

```{.r .cell-code}
ggplot(fl1, aes(x=factor(carrier), y=arr_delay))+
geom_boxplot(fill="skyblue", color="black")+
ylim(-87,1273)
```

::: {.cell-output-display}
![](flights_files/figure-html/unnamed-chunk-5-1.png){width=672}
:::
:::



## Conclusion

Looks like AS, HA, and OO Carriers are doing comparily well on not having so much delay on arrival.



::: {.cell}

:::