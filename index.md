---
title       : Belgian Baby Names Shiny App
subtitle    : Coursera Developing Data Products Course Project
author      : Robert Emerencia
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Belgium

- Known for its famous
    - Fries
    - Chocolates
    - Beers
- But what do you know about Belgian... *data?*
- Goal of this Shiny app: analyze *popular Belgian baby names*!
containing `ui.R` and `server.R`

--- .class #id 

## Some facts
- Three regions in Belgium
    - Flemish Region (6.5M inhabitants, language: Dutch)
    - Walloon Region (3.6M inhabitants, languages: 98% French, 2% German)
    - Brussels-Capital Region (1.2M inhabitants, languages: 80% French, 20% Dutch)
- Statistics Belgium: http://statbel.fgov.be/ (open data)
    - Population statistics: births, buildings counts, ...
    - Labour market: incomes, education,...
    - Other categories: Economy, Transport, Environment, Energy
- We'll use the [First names of newborns 1995-2015](http://statbel.fgov.be/nl/modules/publications/statistiques/bevolking/bevolking_-_voornamen_van_de_pasgeborenen_1995-2014.jsp) dataset (2 Excel files)

--- .class #id 

## About the application
- Input datasets after preprocessing (csv)
    - boy name stats per region & year
    - girl name stats per region & year
    - list of unique boy/girl names
- Feature 1: top 10/20 baby names for given gender/region/period
- Feature 2: statistics for a particular baby name
    - name suggestions based on a search term and a string distance calculation
    (see next slide)
    - statistic 1: number of newborns per year
    - statistic 2: 'popularity score' of a name (see next slide)

--- .class #id 

## Some specifics
### Finding baby names based on a search term: Levenshtein distance

```r
searchTerm <- "John"
exampleNames <- c("Robert", "John", "Johnny", "Johannes", "Johan", "Sulayman")
as.vector(adist(searchTerm, exampleNames)) # best matches: John (2) and Johan (5)
```

```
## [1] 5 0 2 4 1 7
```
### Popularity score of a name

```r
# Example: list of 15 names for which we calculate the popularity score of the
# name with the 3rd highest count value (i.e. order of 3)
maxOrder <- 15; nameOrder <- 3; 
popularity <- round(100*(maxOrder - nameOrder + 1)/maxOrder, 1); popularity
```

```
## [1] 86.7
```





