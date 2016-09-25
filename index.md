---
title       : Belgian Baby Names Shiny App
subtitle    : Coursera Developing Data Products Course Project
author      : 
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Belgium

- Known for its famous Belgian
    - Fries
    - Chocolates
    - Beers
- But what do you know about Belgian... *data?*
- Goal of this Shiny app: analyze *popular Belgian baby names*!

--- .class #id 

## Some facts about Belgium
- Divided into 3 regions
    - Flemish Region (6.5M inhabitants, languages: Dutch)
    - Walloon Region (3.6M inhabitants, languages: 98% French, 2% German)
    - Brussels-Capital Region (1.2M inhabitants, languages: 80% French, 20% Dutch)
- Statistics Belgium: http://statbel.fgov.be/ (open data)
    - Population statistics: births, buildings counts, ...
    - Labour market: incomes, education,...
    - Economy: consumer prices, agriculture, ...
    - Other categories: Transport, Environment, Energy

--- .class #id 

## The data we'll use
- [First names of newborns 1995-2015](http://statbel.fgov.be/nl/modules/publications/statistiques/bevolking/bevolking_-_voornamen_van_de_pasgeborenen_1995-2014.jsp)
- Set of 2 Excel files: boy name and girl name counts
    - split per year (period: 1995-2015), and
    - split per region (Flanders, Wallonia, Brussels)


--- .class #id 

## Features of the application
- Tab 1: top 10/20 baby names for given gender/region/period
- Tab 2: statistics for a particular baby name
    - specify a search term and a list of 15 name matches is returned based on 
    a string distance calculation (see next slide)
    - statistic 1: number of newborns per year
    - statistic 2: 'popularity score' of name (see next slide)

--- .class #id 

## Some specifics
### Finding baby names based on a search term: Levenshtein distance

```r
searchTerm <- "John"
exampleNames <- c("Robert", "John", "Johnny", "Johannes", "Johan", "Sulayman")
as.vector(adist("John", exampleNames)) # John (2) and Johan (5) are best matches
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




