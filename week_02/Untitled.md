---
title: "gdp"
execute:
  keep-md: true
  df-print: paged
  warning: false
format:
  html:
    code-fold: true
    code-line-numbers: true
---


::: {.cell}

```{.r .cell-code}
library(gapminder)
library(tidyverse)
```
:::

::: {.cell}

```{.r .cell-code}
gapminder1<-gapminder%>%
  filter(country!="Kuwait")%>%
  mutate(population1 = case_when(pop/100000<10000~10000,
         pop/100000<20000~20000,
         pop/100000<30000~30000))
gapminder2<-gapminder1%>% 
  group_by(year, continent) %>% 
   summarise(ave = weighted.mean(gdpPercap))
```
:::

::: {.cell}

```{.r .cell-code}
ggplot(data = gapminder1, mapping = aes(x=year, y=gdpPercap, 
                                  color = continent,
                                  size = population1,
                                  line=country)) +
geom_point() +
geom_line(size=.3) +
scale_x_continuous()+
scale_y_continuous() +
labs(x= "Year",
     y = "GDP per Capita",
     size = "Population (100K)",
     color = "continent") + 
  theme_bw() +
facet_wrap(~continent, nrow=1)
```

::: {.cell-output-display}
![](Untitled_files/figure-html/unnamed-chunk-3-1.png){width=960}
:::
:::

::: {.cell}

```{.r .cell-code}
 geom_hline(data = gapminder2,
                mapping = aes(y=gdpPercap)) 
```

::: {.cell-output .cell-output-stdout}
```
mapping: y = ~gdpPercap 
geom_hline: na.rm = FALSE
stat_identity: na.rm = FALSE
position_identity 
```
:::
:::

::: {.cell}

:::