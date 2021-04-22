dplyr Joins
================

## Introduction

A major hurdle for non-technical folks is to understand Joins in the
dplyr package. The objective of this repo is to visualize the joins
hoping to bring clarity to such folks, including me in some cases.

## Left Join

Here, we will define the two tables `df1` and `df2` and perform a
`left_join` on them.

``` r
df1 <- data.frame(id = 1:5,
                  x = paste0("x", 1:5),
                  y = paste0("y", 1:5))

df2 <- data.frame(id = c(1,3),
                  z = c("z1","z3"))

df3 <- left_join(df1, df2, by = "id")

SVG(width = 700, height = 350) %>% 
  svg_sub_table(df = df1)  %>% 
  svg_sub_table(df = df2, x = 200) %>% 
  svg_sub_table(df = df3, x = 350)
```

<svg width="700" height="350">
  <rect x="50" y="50" width="50" height="50" stroke="grey" fill="blue"/>
  <text x="66.5" y="83" font-family="helvetica" font-size="20" font-weight="bold">id</text>
  <rect x="100" y="50" width="50" height="50" stroke="grey" fill="blue"/>
  <text x="116.5" y="83" font-family="helvetica" font-size="20" font-weight="bold">x</text>
  <rect x="150" y="50" width="50" height="50" stroke="grey" fill="blue"/>
  <text x="166.5" y="83" font-family="helvetica" font-size="20" font-weight="bold">y</text>
  <rect x="50" y="100" width="50" height="50" stroke="grey" fill="white"/>
  <text x="66.5" y="133" font-family="helvetica" font-size="20">1</text>
  <rect x="100" y="100" width="50" height="50" stroke="grey" fill="white"/>
  <text x="116.5" y="133" font-family="helvetica" font-size="20">x1</text>
  <rect x="150" y="100" width="50" height="50" stroke="grey" fill="white"/>
  <text x="166.5" y="133" font-family="helvetica" font-size="20">y1</text>
  <rect x="50" y="150" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="66.5" y="183" font-family="helvetica" font-size="20">2</text>
  <rect x="100" y="150" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="116.5" y="183" font-family="helvetica" font-size="20">x2</text>
  <rect x="150" y="150" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="166.5" y="183" font-family="helvetica" font-size="20">y2</text>
  <rect x="50" y="200" width="50" height="50" stroke="grey" fill="white"/>
  <text x="66.5" y="233" font-family="helvetica" font-size="20">3</text>
  <rect x="100" y="200" width="50" height="50" stroke="grey" fill="white"/>
  <text x="116.5" y="233" font-family="helvetica" font-size="20">x3</text>
  <rect x="150" y="200" width="50" height="50" stroke="grey" fill="white"/>
  <text x="166.5" y="233" font-family="helvetica" font-size="20">y3</text>
  <rect x="50" y="250" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="66.5" y="283" font-family="helvetica" font-size="20">4</text>
  <rect x="100" y="250" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="116.5" y="283" font-family="helvetica" font-size="20">x4</text>
  <rect x="150" y="250" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="166.5" y="283" font-family="helvetica" font-size="20">y4</text>
  <rect x="50" y="300" width="50" height="50" stroke="grey" fill="white"/>
  <text x="66.5" y="333" font-family="helvetica" font-size="20">5</text>
  <rect x="100" y="300" width="50" height="50" stroke="grey" fill="white"/>
  <text x="116.5" y="333" font-family="helvetica" font-size="20">x5</text>
  <rect x="150" y="300" width="50" height="50" stroke="grey" fill="white"/>
  <text x="166.5" y="333" font-family="helvetica" font-size="20">y5</text>
  <text x="50" y="45" font-family="helvetica" font-size="12">df1</text>
  <rect x="250" y="50" width="50" height="50" stroke="grey" fill="blue"/>
  <text x="266.5" y="83" font-family="helvetica" font-size="20" font-weight="bold">id</text>
  <rect x="300" y="50" width="50" height="50" stroke="grey" fill="blue"/>
  <text x="316.5" y="83" font-family="helvetica" font-size="20" font-weight="bold">z</text>
  <rect x="250" y="100" width="50" height="50" stroke="grey" fill="white"/>
  <text x="266.5" y="133" font-family="helvetica" font-size="20">1</text>
  <rect x="300" y="100" width="50" height="50" stroke="grey" fill="white"/>
  <text x="316.5" y="133" font-family="helvetica" font-size="20">z1</text>
  <rect x="250" y="150" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="266.5" y="183" font-family="helvetica" font-size="20">3</text>
  <rect x="300" y="150" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="316.5" y="183" font-family="helvetica" font-size="20">z3</text>
  <text x="250" y="45" font-family="helvetica" font-size="12">df2</text>
  <rect x="400" y="50" width="50" height="50" stroke="grey" fill="blue"/>
  <text x="416.5" y="83" font-family="helvetica" font-size="20" font-weight="bold">id</text>
  <rect x="450" y="50" width="50" height="50" stroke="grey" fill="blue"/>
  <text x="466.5" y="83" font-family="helvetica" font-size="20" font-weight="bold">x</text>
  <rect x="500" y="50" width="50" height="50" stroke="grey" fill="blue"/>
  <text x="516.5" y="83" font-family="helvetica" font-size="20" font-weight="bold">y</text>
  <rect x="550" y="50" width="50" height="50" stroke="grey" fill="blue"/>
  <text x="566.5" y="83" font-family="helvetica" font-size="20" font-weight="bold">z</text>
  <rect x="400" y="100" width="50" height="50" stroke="grey" fill="white"/>
  <text x="416.5" y="133" font-family="helvetica" font-size="20">1</text>
  <rect x="450" y="100" width="50" height="50" stroke="grey" fill="white"/>
  <text x="466.5" y="133" font-family="helvetica" font-size="20">x1</text>
  <rect x="500" y="100" width="50" height="50" stroke="grey" fill="white"/>
  <text x="516.5" y="133" font-family="helvetica" font-size="20">y1</text>
  <rect x="550" y="100" width="50" height="50" stroke="grey" fill="white"/>
  <text x="566.5" y="133" font-family="helvetica" font-size="20">z1</text>
  <rect x="400" y="150" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="416.5" y="183" font-family="helvetica" font-size="20">2</text>
  <rect x="450" y="150" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="466.5" y="183" font-family="helvetica" font-size="20">x2</text>
  <rect x="500" y="150" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="516.5" y="183" font-family="helvetica" font-size="20">y2</text>
  <rect x="550" y="150" width="50" height="50" stroke="grey" fill="grey"/>
  <text x="566.5" y="183" font-family="helvetica" font-size="20">NA</text>
  <rect x="400" y="200" width="50" height="50" stroke="grey" fill="white"/>
  <text x="416.5" y="233" font-family="helvetica" font-size="20">3</text>
  <rect x="450" y="200" width="50" height="50" stroke="grey" fill="white"/>
  <text x="466.5" y="233" font-family="helvetica" font-size="20">x3</text>
  <rect x="500" y="200" width="50" height="50" stroke="grey" fill="white"/>
  <text x="516.5" y="233" font-family="helvetica" font-size="20">y3</text>
  <rect x="550" y="200" width="50" height="50" stroke="grey" fill="white"/>
  <text x="566.5" y="233" font-family="helvetica" font-size="20">z3</text>
  <rect x="400" y="250" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="416.5" y="283" font-family="helvetica" font-size="20">4</text>
  <rect x="450" y="250" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="466.5" y="283" font-family="helvetica" font-size="20">x4</text>
  <rect x="500" y="250" width="50" height="50" stroke="grey" fill="powderblue"/>
  <text x="516.5" y="283" font-family="helvetica" font-size="20">y4</text>
  <rect x="550" y="250" width="50" height="50" stroke="grey" fill="grey"/>
  <text x="566.5" y="283" font-family="helvetica" font-size="20">NA</text>
  <rect x="400" y="300" width="50" height="50" stroke="grey" fill="white"/>
  <text x="416.5" y="333" font-family="helvetica" font-size="20">5</text>
  <rect x="450" y="300" width="50" height="50" stroke="grey" fill="white"/>
  <text x="466.5" y="333" font-family="helvetica" font-size="20">x5</text>
  <rect x="500" y="300" width="50" height="50" stroke="grey" fill="white"/>
  <text x="516.5" y="333" font-family="helvetica" font-size="20">y5</text>
  <rect x="550" y="300" width="50" height="50" stroke="grey" fill="grey"/>
  <text x="566.5" y="333" font-family="helvetica" font-size="20">NA</text>
  <text x="400" y="45" font-family="helvetica" font-size="12">df3</text>
</svg>
