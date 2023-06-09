---
title: "Computations"
format: html
editor: visual
date: "April 21, 2023"
execute:
  keep-md: true
  format:
  html:
    code-fold: true
    code-line-numbers: true
---


---

## Quarto

Quarto enables you to weave together content and executable code into a finished document. To learn more about Quarto see <https://quarto.org>.

## Running Code

When you click the **Render** button a document will be generated that includes both content and the output of embedded code. You can embed code like this:

::: {.cell}

```{.r .cell-code}
1 + 1+1+1+1+1
```

::: {.cell-output .cell-output-stdout}
```
[1] 6
```
:::
:::

You can add options to executable code like this

::: {.cell}
::: {.cell-output .cell-output-stdout}
```
[1] 4
```
:::
:::



The `echo: false` option disables the printing of code (only output is displayed).

::: {.cell}

:::