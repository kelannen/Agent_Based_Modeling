# Data Science Insights 2:

## od:

od is an R package that was published on September 9th, 2020. The main purpose of this package is to manipulate and map origin-destination data. It specifically aims to provide
tools and examples of data sets for when one is working with origin-destination or OD datasets with a focus on those used to descibe and approximate movement patterns in urban
areas. 

The od package itself builds on existing functions in the package stplanr that work on OD data and make them more efficient computationally and supportive of the sf class
system. od is meant to help with the analysis of OD datasets and also give a place for people to develop new functions to continue improving the handiling of those datasets. 
Allowing the creation and analysis of geographic locations and the mobility patterns, from day to day to moving to another country, is really applicable to what we have been
doing in project 3 so far and also the important concept of human movement in agent based modeling. 

As mentioned above the od package builds off of the stplanr package and supports the sf class system, but it also includes concpets from a paper about aggregate urban mobility 
patterns. If you would like to look at this paper, it is the third link down below. To quickly summarize the paper, it suggests a way to estimate origin and destination
volumes based off of a direct demand function and incomplete aggregate data.

There already exists a vignette that goes more into depth about the od package as well as how to use it. You can find and take a look at this for yourself using the last link 
down below. Note, as this is a good example of how to use the package and explains it more in depth, I have decided not to do so in this writeup. This vignette also contains some
links to other resources you may find helpful about the background of this package and some of its various use cases. 

I will have to look more into the package and how to use it as well as the paper the package is based off of, but I believe that it is relevant to the project we are working
on now in class and think it is interesting to see a new package addressing the same sort of problem.

## Links:

https://rviews.rstudio.com/2020/10/23/sept-2020-top-40-new-cran-packages/

https://cran.r-project.org/web/packages/od/index.html

https://pubsonline.informs.org/doi/abs/10.1287/trsc.15.1.32

https://cran.r-project.org/web/packages/od/vignettes/od.html
