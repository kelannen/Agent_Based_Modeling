# Project 2

For Project 2, I decided to continue with Cote D’Ivoire. I originally requested access to the just the survey data without GPS or other components. I have put my proposal to request this data down below. 

The purpose of this research is to improve upon the use of multinomial logistic regression models to generate a closer-to-reality synthetic population by specifying, estimating and validating
a continuous spatial model as compared to my previous work estimating a discretized spatial model. I will use remotely sensed data to estimate all dwelling unit locations
across Cote d'Ivoire and survey data to estimate a spatially continuous multinomial logistic regression model for predicting household size, gender and age of all dwelling units across Cote d'Ivoire.

After receiving access to the personal and household survey information I looked at the .dto as well as the documentation about the survey to understand what data I was working with. There were 9686 households represented in the dataset with 3900 different columns representing possible variables. I also noticed that the data only contained information about which region it was from and did not contain anything about which administrative levels (1 or 2) it belonged to. As such, I requested the GPS data for Cote D’Ivoire to see if that would help my pinpoint the different administrative levels. Unfortunately, it did not contain that info but I was able to figure out which administrative level 1’s went to that region due to overlaying maps and additional research. Throughout project 2 this led to dealing with massive amounts of data and additional considerations that I will detail throughout this report. 

The sum of the size column in the household’s dataset gave the total number of persons observed, which is 51187 individuals. I have listed other important columns/variables that were considered throughout project 2.

Household ID: hhid, Unit: hv004, Survey weights: hv005/1000000, # of household members: hv009, Location: hv024 (as I mentioned before this was just the different regions in Cote D’Ivoire, Gender of household members: columns 294-329, age of household members: columns 330-365, highest education level attained: columns 474-509, and Wealth: hv270

The gender, age, and education variables each consisted of 35 columns as the household that had the largest number of residents was 35 and therefore it was necessary to have 35 columns to account for each individual household member. The sum of the weights equaled 9686, which is the same number as the number of households. Pivoting the data to be based upon each column (age, gender, education, wealth) individually, and then recombing them enabled me to create a data frame with persons and their individual attributes rather than have them hidden within a singular household. However, I did have to account for the fact that some of the pivot tables had more rows than the others and created id’s to merge them on using hhid and pumbr to make sure that all three pivot tables came out to be the same number of rows. Through this method approximately 200 rows were dropped, however as number of rows in the combined pivot table was 51173, this didn’t seem to affect the accuracy of the data from there on. The number of rows after pivoting 51173 was very close in comparison to the number of individuals (which is 51187). Changing from households to individuals introduces some error into the data set created by the survey. While this does introduce some inaccuracies into the analysis and prediction later on the person-sample proportion was 0.00198. This means that the survey was still only about 0.198% of the actual population of Cote D’Ivoire. In general, it would be best to try and increase this percentage as much as possible to get a more accurate depiction of the country.  

To get the spatially located households at administrative level zero of Cote D’Ivoire, I calculated the average number of households as the sum of the population raster divided by the mean of the household size of the DHS data. From there, I generated a randomly generated points and number of households with the population raster as the density file and the Cote D’Ivoire shape file as the window. The x and y coordinates made up the adm0. The weighted error after doing all of this and pivoting was 0.0003388086. Which was really good. Ironically, computing at the adm0 level was less computationally expensive than that at the adm1 level.

This and the next step are where the downsides of not being able to filter by administrative levels really hindered my ability to complete and analyze the data. This is due to the fact that there were two administrative level ones in the region I was focusing on, nord ouest, the memory and computation costs were a lot larger and, in some areas, prevented me from being able to accomplish some of the finer details. To try and handle some of the areas I increased the max memory size of the RStudio session so that it would be able to compute and then load data frames that had GB of data. This was necessary when creating and then attempting to merge the pivot tables to get pns during this step in the process. It took my computer around 2 hours to compute the pns for Cote D’Ivoire nord ouest when there was only gender and age. Unfortunately, I was unable to get it to merge education into the this pns even with the extended memory size as it took way too much CPU, memory, and time for it to run. To try and handle this I decided to keep wealth as a column in one of the pivot tables and not the other one. I also made sure instead of keeping two copies of the duplicate columns (such as location or hhid) that only one was kept to try and minimize size. After doing this I was able to get some of the statistics about the synthetically generated households and persons. First the weights of the pns was 20692661 while the number of rows (the number of individuals accounted for) in the pns was 21234728. This pns had a generated synthetic person total proportion to ML/EO output of 15.98283, compared to the DHS-based 0.19. I think the generated households and persons at the administrative one level is more accurate than the one at the administrative zero level as it has a higher ML/EO output and is more specific on the location and some of the other variables. To further improve the measures of accuracy, I would have looked for more ways to narrow the scope of the location to a single administrative one level instead of having it divided over two. This would have helped because the amount of computation power, memory, and time different aspects would have taken me to run would have enabled me to test and try out different options instead of being stuck with only doing one or two different ways and just comparing those and also having to limit the number of variables in the pns itself.

Compared to a randomly generated synthetic population that attempts to describe the demographic attributes of households and persons, the generated synthetic population that I was able to come up with more closely approximates reality. This is because it uses weights and more information to come up with better distributions. However, as it is based on survey data some aspects of it may be incorrect or inaccurate. Accurate, complete, and updated census data would have helped generate synthetic population that is closest to approximating reality. However, it is unrealistic to have that due to time and cost. Unfortunately, due to the quantity of data that I was handling (as mentioned earlier in this report), it was hard to train and test the data and then display this information. Training the different models alone was taking a minimum of 30 minutes and it was very taxing on my computer. There were some positives of this as it seemed to help make my population more accurate however it was mostly negative as it prevented me from completing this part of the project. Next time I would try to figure out a way to narrow/divide the region into a singular administrative one level even though that would introduce some errors as it would help the model to be more useful than it currently is. 

The closest I was able to get to graphs was at the stage below with its associated output. As mentioned earlier I decided to use/predict wealth as my computer was unable to handle the memory, computation, and time costs associated with using and predicting the highest education level received. I also was unable to get the plots as a fatal error occurred and I had to have a new R session when I tried to plot the different models and its results.

nord_ouest_pns2_mnlr %>%                                                    A tibble: 2 x 3
  predict(nord_ouest_pns2_testing) %>%                                      .metric  .estimator .estimate
  bind_cols(nord_ouest_pns2_testing) %>%                                    <chr>    <chr>          <dbl>
  metrics(truth = wealth, estimate = .pred_class)                             1 accuracy multiclass    0.246 
                                                                              2 kap      multiclass    0.0354

nord_ouest_pns2_ranger %>%                                                  A tibble: 2 x 3
  predict(nord_ouest_pns2_testing) %>%                                      .metric  .estimator .estimate
  bind_cols(nord_ouest_pns2_testing) %>%                                    <chr>    <chr>          <dbl>
  metrics(truth = wealth, estimate = .pred_class)                           1 accuracy multiclass     0.288
                                                                            2 kap      multiclass     0.101

Last but not least, below are some of the different images that I generated of households over Cote D’Ivoire.

#### Cote D’Ivoire pipo
![](https://kelannen.github.io/Agent_Based_Modeling/Project_2/cd_pipo.png)

#### Cote D’Ivoire Houselocs Using BaseR
![](https://kelannen.github.io/Agent_Based_Modeling/Project_2/houselocs_cd_no_using_baseR.png)

#### Cote D’Ivoire Household Distribution
![](https://kelannen.github.io/Agent_Based_Modeling/Project_2/cote_divoire_household_distribution.png)

#### Cote D’Ivoire Nord Ouest Using Spatstat
![](https://kelannen.github.io/Agent_Based_Modeling/Project_2/using_spatstat_nord_ouest_houses.png)

#### Cote D’Ivoire Nord Ouest Household Distribution
![](https://kelannen.github.io/Agent_Based_Modeling/Project_2/cote_diboire_nord_ouest_household_distribution.png)

#### Cote D’Ivoire adm1 accuracy
![](https://kelannen.github.io/Agent_Based_Modeling/Project_2/cd_no_adm1_error1.png)
![](https://kelannen.github.io/Agent_Based_Modeling/Project_2/cd_no_error2.png)
