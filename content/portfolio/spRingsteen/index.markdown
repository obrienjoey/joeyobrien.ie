---
title: spRingsteen
author: ''
date: '2022-05-04'
slug: []
categories: []
tags: []
subtitle: 'Scraping all things data about the Boss - Bruce Springsteen, wrapped in a tidy-friendly R package.'
summary: 'Scraping all things data about the Boss - Bruce Springsteen, wrapped in a tidy-friendly R package.'
authors: []
lastmod: '2022-05-04T22:02:41Z'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---



We all love him --- if you disagree you just haven't spent long enough listening --- it is of course the Boss, the Jersey Devil, Bruce Springsteen. With a musical career spanning over fifty years, record breaking albums, an award-winning one-man Broadway show, podcast series with ex-Presidents and so much more. However what Bruce (I hope he is okay with me working on first name terms) is most famous for is his live performances. Hard rocking four hour sets, solo acoustic shows, country swing bands, the list goes on and on but throughout his career there has been a huge collection of performances with ever-changing setlists working there way through both his own recording history and also the classics from other artists.

<p align="center">
  <img src="https://media.giphy.com/media/H89Osb5ZHntuCJHFRE/giphy.gif" alt="animated" />
</p>

Thankfully, this huge repertoire of performances have been carefully collected by the devoted followers on E Street through the fan site [Brucebase](http://brucebase.wikidot.com/). Within this platform is a huge collection of data describing the majority of shows the Boss has ever performed including ever song performed at each gig. This source of data is what makes up the spRingsteen `R` package which I have created to allow for the data inclined to analyse both quickly and in a reproducible manner. In this post I discuss the data collection alongside its storage in a SQL setting, the process of wrapping the data in an `R` package and a quick demonstration of some possible data analysis that can be performed with it.

### Data collection and database storage

As mentioned before, the goldmine needed for this project is Brucebase - a fan led platform containing a huge collection of data describing the Springsteen career over the past 50  years. Given that this data is readily available via this online platform it can be collected rather quickly via web-scraping. This is the idea of setting up a computer program to literally scrape, or collect, the content from a website and store it in an accessible manner. 

The main idea is to find a systematic approach towards accessing the entire corpus of setlists, thankfully the maintainers of the site structure the URL associated with each page such that the date and venue of the concert is the main identifier, for example <http://brucebase.wikidot.com/gig:2016-05-27-croke-park-dublin-ireland>. As such, if the date and location of each performance is known the setlists can then be readily accessed. Fortunately, there are separate pages (found [here](http://brucebase.wikidot.com/stats:tour-statistics)) which simply contain these exact values, so the first thing is to collect these values which then feed the setlist collector. Using the `R` packages `rvest` and `dplyr` this can be done rather quickly.

It is important to note however that there is quite a lot of data here, with over 50 years of performances, 25 tours, and over 1,500 songs. As such the storage of the data is important, classical spreadsheets can of course be used however more standard approaches for such data, particularly given that there are multiple tables (setlists, song details, venues and dates) is in a database setting. This is where the `DBI` and `RSQLite` packages comes into play where we can perform work with reading/writing a database directly in `R`.


```r
### we connect to a database like so

db_loc = here('database/springsteen_data.sqlite')
springsteen_db = DBI::dbConnect(RSQLite::SQLite(), db_loc)

### concert_df would be a tibble containing the collected data
### which we now write to the "concerts" table in the database

DBI::dbWriteTable(springsteen_db, 
                  "concerts",
                  concert_df)

### and finally close the database connection

DBI::dbDisconnect(springsteen_db)
```

So we can collect all the data we need from Brucebase, parse it in a tidy format and write to a database all within `R`, what a language! This is exactly what happens in the [**springsteen_db**](https://github.com/obrienjoey/springsteen_db) repository hosted on my Github. There is also some very nice automation hosted within there such that the scripts are run every day to check if the Boss has had any new shows and if so that data also gets added to the database. 

### Creating a data-centric R package

Now with the data in place and neatly stored within a repository anyone can quickly load it into their programming language of choice, however I thought it would be particularly nice if it was accessible directly in `R` via its very own package. In order to perform such development work we are extremely fortunate in the `R`-universe to have packages like `usethis` which take away a lot of the pain from package creation with a huge array of tools. The main emphasis - as any data scientist/engineer has no doubt been told by their software developer peers (if fortunate enough to work alongside some) - is documentation. Each dataset in my case, and how it originated, has to be described in detail alongside toy examples to demonstrate possible use cases of the data.

Indeed, `usethis` also offers functionality that allows for the package to be based upon a Github repository for future maintenance and also allows for it to be accessed in its latest form via


```r
remotes::install_github("obrienjoey/spRingsteen")
```

However for a package to be really picked up I believe it needs to be hosted on CRAN, the official `R` package platform. Again, `usethis` offers a range of functionality to prepare the new package for submission, where it goes through extensive validation and testing on a range of environments from the team there. All going well with documentation and the package performing correctly within the different tests on CRAN the work will get accepted and have its very own page [like so](https://cran.r-project.org/web/packages/spRingsteen/index.html).

### Example analysis

So having collected the data and developed a package we are now left with the fun part - playing with the data! So let's load in the package directly from CRAN and have a look at some example data analysis we can do straight away. For example let's check out the top 10 most played songs by Springsteen through out his career:


```r
library(spRingsteen)

spRingsteen::setlists |> 
  count(song, sort = TRUE) |>
  slice(1:10) |> 
  mutate(song = ifelse(song == 'Born In The U.s.a.', 'Born In The U.S.A.', song),
         song = forcats::fct_rev(forcats::fct_inorder(song))) |> 
  ggplot(aes(x = n, y = song)) +
  geom_col(fill = '#2176FF') +
  geom_text(aes(label = n), 
            hjust = 0, nudge_x = .5,
            size = 4, fontface = "bold", family = "Fira Sans") +
  coord_cartesian(clip = "off") +
  scale_x_continuous(expand = c(.01, .01)) +
  theme_void() +
  theme(
    axis.text.y = element_text(size = 14, hjust = 1, family = "Fira Sans"),
    plot.margin = margin(15, 30, 15, 15)
  )
```

<img src="staticunnamed-chunk-3-1.png" width="672" style="display: block; margin: auto;" />

### Conclusions

I hope this summary gave you a nice insight into the **spRingsteen** package (and hopefully has you inspired for a quick check in on the Boss). Overall it is a dense data engineering project involving setting up an automated scraper that can collect all the data needed, storage in a SQL database, and a nice wrapping in a `R` package. All of the code can be found on my Github and hopefully it can help in setting up similar pipelines, because remember - you can't start a fire without a spark. 
