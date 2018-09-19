hw01\_gapminder
================

Exploration of the gapminder data set
-------------------------------------

This is a brief exploration of the gapminder dataset. First, let's load the library:

``` r
library(gapminder)
library(tidyverse)
```

    ## -- Attaching packages ---------------------------------------------------------------------------------------------------------- tidyverse 1.2.1 --

    ## v ggplot2 2.2.1     v purrr   0.2.5
    ## v tibble  1.4.2     v dplyr   0.7.4
    ## v tidyr   0.8.1     v stringr 1.3.0
    ## v readr   1.1.1     v forcats 0.3.0

    ## -- Conflicts ------------------------------------------------------------------------------------------------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

Summary of gapminder dataset:
-----------------------------

``` r
summary(gapminder)
```

    ##         country        continent        year         lifeExp     
    ##  Afghanistan:  12   Africa  :624   Min.   :1952   Min.   :23.60  
    ##  Albania    :  12   Americas:300   1st Qu.:1966   1st Qu.:48.20  
    ##  Algeria    :  12   Asia    :396   Median :1980   Median :60.71  
    ##  Angola     :  12   Europe  :360   Mean   :1980   Mean   :59.47  
    ##  Argentina  :  12   Oceania : 24   3rd Qu.:1993   3rd Qu.:70.85  
    ##  Australia  :  12                  Max.   :2007   Max.   :82.60  
    ##  (Other)    :1632                                                
    ##       pop              gdpPercap       
    ##  Min.   :6.001e+04   Min.   :   241.2  
    ##  1st Qu.:2.794e+06   1st Qu.:  1202.1  
    ##  Median :7.024e+06   Median :  3531.8  
    ##  Mean   :2.960e+07   Mean   :  7215.3  
    ##  3rd Qu.:1.959e+07   3rd Qu.:  9325.5  
    ##  Max.   :1.319e+09   Max.   :113523.1  
    ## 

Let's select the variable year:
-------------------------------

``` r
select(gapminder, year)
```

    ## # A tibble: 1,704 x 1
    ##     year
    ##    <int>
    ##  1  1952
    ##  2  1957
    ##  3  1962
    ##  4  1967
    ##  5  1972
    ##  6  1977
    ##  7  1982
    ##  8  1987
    ##  9  1992
    ## 10  1997
    ## # ... with 1,694 more rows

Now let's list country first and then list everything else:
-----------------------------------------------------------

``` r
select(gapminder, country, everything())
```

    ## # A tibble: 1,704 x 6
    ##    country     continent  year lifeExp      pop gdpPercap
    ##    <fct>       <fct>     <int>   <dbl>    <int>     <dbl>
    ##  1 Afghanistan Asia       1952    28.8  8425333      779.
    ##  2 Afghanistan Asia       1957    30.3  9240934      821.
    ##  3 Afghanistan Asia       1962    32.0 10267083      853.
    ##  4 Afghanistan Asia       1967    34.0 11537966      836.
    ##  5 Afghanistan Asia       1972    36.1 13079460      740.
    ##  6 Afghanistan Asia       1977    38.4 14880372      786.
    ##  7 Afghanistan Asia       1982    39.9 12881816      978.
    ##  8 Afghanistan Asia       1987    40.8 13867957      852.
    ##  9 Afghanistan Asia       1992    41.7 16317921      649.
    ## 10 Afghanistan Asia       1997    41.8 22227415      635.
    ## # ... with 1,694 more rows

We'll arrange the dataset in descending order based on population:
------------------------------------------------------------------

``` r
arrange(gapminder, desc(pop))
```

    ## # A tibble: 1,704 x 6
    ##    country continent  year lifeExp        pop gdpPercap
    ##    <fct>   <fct>     <int>   <dbl>      <int>     <dbl>
    ##  1 China   Asia       2007    73.0 1318683096     4959.
    ##  2 China   Asia       2002    72.0 1280400000     3119.
    ##  3 China   Asia       1997    70.4 1230075000     2289.
    ##  4 China   Asia       1992    68.7 1164970000     1656.
    ##  5 India   Asia       2007    64.7 1110396331     2452.
    ##  6 China   Asia       1987    67.3 1084035000     1379.
    ##  7 India   Asia       2002    62.9 1034172547     1747.
    ##  8 China   Asia       1982    65.5 1000281000      962.
    ##  9 India   Asia       1997    61.8  959000000     1459.
    ## 10 China   Asia       1977    64.0  943455000      741.
    ## # ... with 1,694 more rows

Finally let's find all entries of Brazil and Germany occuring in the '80s:
--------------------------------------------------------------------------

``` r
gapminder %>% 
  filter((country == "Brazil" | country == "Germany") & year >= 1980 & year < 1990 )
```

    ## # A tibble: 4 x 6
    ##   country continent  year lifeExp       pop gdpPercap
    ##   <fct>   <fct>     <int>   <dbl>     <int>     <dbl>
    ## 1 Brazil  Americas   1982    63.3 128962939     7031.
    ## 2 Brazil  Americas   1987    65.2 142938076     7807.
    ## 3 Germany Europe     1982    73.8  78335266    22032.
    ## 4 Germany Europe     1987    74.8  77718298    24639.
