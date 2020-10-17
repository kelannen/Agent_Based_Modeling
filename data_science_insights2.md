# Data Science Insights 2:

## sdglinkage:

sdklinkage is an R package that was published on April 27th, 2020. It provides a tool for synthetic data generation that can be used for linkage method development with elements of gold standard file with complete and accurate information or two linkage files that are corrupted as we often see in the raw dataset. 

The linkage of administrative sources makes it easier to tackle research on large populations and minimizes the amounts of time and the financial burden that is involved in more traditional methods of data collection. It is important to consider cases where unique identifiers are not available especially when trying to create various ways to link the data as otherwise bias as a result form linkage errors will be present. 

There are different tutorials and guides on how to use the sdklinkage package to accomplish various main tasks. I will link these tutorials down below so that you can look at the different ways this package can be applied and its result.

Going back to the main sdklinkage package, there are some basics ideas of workflows that the package supports. One of these things is looking at the different types of classes there are and what functions they use. Some of the main types of functions the file has are: acquire error flags, add error flags, mask sensitive variables, synthetic data generator, synthetic data evaluation, custom generation rules, and damage actions.  

As I mentioned earlier there are already guides that are able to walk you through how to use sdklinkage, these guides focus on three main cases for this package. The first case for the package was synthetic data generation and evaluation which shows how to generate data and evaluate that data’s quality. The next case was the generation of gold standard file and library to show how to generate synthetic complete and the final one was to show how to generate synthetic identifiers when we have sensitive identifies. 

These different roles all relate back to what we are doing and learning in class about generating synthetic populations. I will have to do more research in how it differentiates itself from those other and more manual methods that we did to basically accomplish the same thing.

## Links:

https://cran.r-project.org/web/packages/sdglinkage/index.html

https://cran.r-project.org/web/packages/sdglinkage/vignettes/sdglinkage_README.html#4_vignette

https://cran.r-project.org/web/packages/sdglinkage/vignettes/Synthetic_Data_Generation_and_Evaluation.html

https://cran.r-project.org/web/packages/sdglinkage/vignettes/From_Sensitive_Real_Identifiers_to_Synthetic_Identifiers.html
