# Project 3

## London Gravity Model Analysis
For the first part of project 3 we followed a guide by Adam Dennett, “Dr. D’s Idiots Guide to Spatial Interaction Modelling for Dummies”, in which we created a gravity model for 
London. The guide had us download and filter data from UK government office of national statistics to get the administrative subdivisions of London and its different boroughs
along with commuter data from the 2001 England and Wales Census. After getting and formatting the data, we calculated a distance matrix which showed the distance between every
possible combination of boroughs being the origin and the destination in London. Next, we created flow estimates using the commuter data and created the total flows column by 
combining the distances and flows between each borrow. The guide then explained how to create the gravity model and the gravity model's equation. This equation was also 
described by Garcia et al in the paper “Modeling Internal Migration Flows in Sub-Saharan Africa Using Census Microdata” which can be summarized as migration between two places
is proportional to the population at the origin/destination and the inverse of the distance between the two points. Dennett's guide also went over how to estimate, evaluate,
and test the model's estimates and accuracy. 

The Garcia et al. paper mentioned earlier expands on the importance and uses of gravity models, especially in relation to human migration. Gravity models are able to explain
up to 87% of internal migrations and are still capable of predicting flows with sparse data. Gravity models can be used not only to predict but also to explain and understand
human migration patterns. The paper also mentioned the expansion of the model by adding additional characteristics or layers to the model which are factors for migration. These
factors can have a large influence of where people decide to live, for instance employment opportunities and crime rates, and when included in the gravity model it can enable 
a better understanding of the reasoning behind migration patterns but also increase the accuracy of predictions.

Using the information from both the guide by Adam Dennett and the paper by Garcia et al., I moved on to looking at and modeling migration within Côte d'Ivoire and creating 
voronoi polygons for Folon and Kabadougou in Denguélé, Côte d'Ivoire. Folon and Kabadougou being the second level administrative subdivisions in Côte d'Ivoire I selected during
project 1.

## Migration in Côte d'Ivoire ADM 1
For this portion of project 3 where it is looking at migration data/flows, I decided to focus on the first administrative level for Côte d'Ivoire. I downloaded migration flow
data from WorldPop and used the Côte d'Ivoire administrative subdivisions data I had previously downloaded from GADM. Below is the visualization of the migration inflows 
and outflows centered in the middle of each level one administrative subdivision. 

#### Migration Flows in Côte d'Ivoire - 2010
Migration Destination Flows Sum | Migration Origin Flows Sum
--- | ---
![](https://kelannen.github.io/Agent_Based_Modeling/Project_3/project_3_destination_flows_sums.png) | ![](https://kelannen.github.io/Agent_Based_Modeling/Project_3/project_3_origin_flows_sums.png)

Another way to visualizae the in and out migration across the different level one administrative subdivisions in Côte d'Ivoire is down below. In the figure below, the level
one administrative subdivision that has the highest in and out migration is Sassandra-Marahoué. It is notably one of the only subdivisions of this level that has a notable 
amount of in migration. The two subdivisions of this level that have the highest out migration excluding Sassandra-Marahoué are Abidjan and Montagnes.

#### In and Out Migration in Côte d'Ivoire
![](https://kelannen.github.io/Agent_Based_Modeling/Project_3/project_3_image_5.png) | ![](https://kelannen.github.io/Agent_Based_Modeling/Project_3/project_3_image_4.png)
--- | ---

After visualizing the in and out migration across the level one administrative subdivision in Côte d'Ivoire, I downloaded night time light data from WorldPop for Côte d'Ivoire.
Night time lights were the additional factor I decided to include for the gravity model as it can help determine how developed a certain area is which correlates to factors
that may increase how likely someone is to move to or from that location. From there I created an origin destination data frame that included the origin county, the destination 
county, the distance between these counties, the migration, the night time lights, the origin centerpoint, the desitantion center point, and the origin-destination centerpoints.
A sample of this table can be seen down below.

![](https://kelannen.github.io/Agent_Based_Modeling/Project_3/project_3_image_2.PNG)

I also created the origin-destination (OD) matrix for migration flows which you can see down below where each cell in the matrix is the combination of two centerpoints. The row
number is the origin centerpoint while the column number is the desination centerpoint. The value of the cells is the predicted migration from the origin to the destination, for
cells where the origin and destination is one and the same, the values are N/A and will be ignored. The names of the different administrative subdivisions are Abidjan, 
Bas-Sassandra, Comoé, Denguélé,	Gôh-Djiboua, Lacs, Lagunes, Montagnes, Sassandra-Marahoué, Savanes, Vallée du Bandama, Woroba, Yamoussoukro, and Zanzan. 

![](https://kelannen.github.io/Agent_Based_Modeling/Project_3/project_3_image_6.PNG)

After creating the OD matrix for the level one administrative subdivisions, I expanded this matrix while calculating the distance between each origin and destination point.
I also calculated the path between these points which you can see as the lines connecting the different centerpoints in the figure below which are a reflection of the physical 
movement of people amongst administrative subdivisions. You can see the still image of the visualization of the migration flows and paths between level one administrative
subdivisions in Côte d'Ivoire below.

![](https://kelannen.github.io/Agent_Based_Modeling/Project_3/project_3_image_7.png)

The animated version of this data depicts five years of migration flows from 2005 to 2010, to make this more relevant and accurate I would update the data I was using to be 
for the most recent five years of migration data. 

#### Animation of Migration Across Côte d'Ivoire
![](https://kelannen.github.io/Agent_Based_Modeling/Project_3/project_3_animation_3.gif)

This animation does not currently incorporate a gravity model. A gravity model could look take in the distances between points, the night time lights, and other factors and 
let us model and compare the estimates and flows it comes up with compared to the one we see now. This could help us improve the accuracy of the animation while also enabling
us to show different factors for the reasoning of such migration flows. 

## Urbanized Areas and Voronoi Polygons
The first thing I did for this section of project three was importing the de facto settlements (urbanized areas)  and center points from the first project and the synthetically
generated population from the second project. I then combined the data from project 1 and 2 to create the figure you see down below.

![](https://kelannen.github.io/Agent_Based_Modeling/Project_3/project_3_image_0.png)

The final figure down below is my tesselation of Voronoi Polygons for Folon and Kabadougou in Denguélé, Côte d'Ivoire for which I created the urbanized areas and synthetic 
population you see in the figure above. I used the center points of each of the settlements to produce the voronoi tesselation of this higher resolution administrative 
subdivision. 

#### Tesselation of Voronoi Polygons for Folon and Kabadougou in Denguélé, Côte d'Ivoire
![](https://kelannen.github.io/Agent_Based_Modeling/Project_3/project_3_image_1.png)

To build an OD matrix for this higher resolution administrative subdivision I would subset the migration flow data for Côte d'Ivoire to just include data for these groupings. 
I would potentially have to find more, higher resolution data but I believe the data I currently have would work. Next, I would calculate the distance between every combination
the settlements for this subdivision. As I already retrieved the transportation data for the roads and also the information about hospitals in this subsection, I could include
those in a gravity model for this subdivsion to make it more accurate. I would also want to include migration to and from outside of this current subsection as it is can 
increase the usefulness of this model.

## Sources:

- [“Dr. D’s Idiots Guide to Spatial Interaction Modelling for Dummies”][1]
- [“Modeling Internal Migration Flows in Sub-Saharan Africa Using Census Microdata”][2]
- [GADM data][3]
- [World Pop][4]
- [Migration Flows Data][5]
- [Night Time Lights Data][6]
- [DHS data][7]

[1]: https://rpubs.com/adam_dennett/257231
[2]: https://academic.oup.com/migration/article/3/1/89/2413406
[3]: https://gadm.org/download_country_v3.html
[4]: https://www.worldpop.org/geodata/summary?id=6097
[5]: https://www.worldpop.org/geodata/summary?id=1281
[6]: https://www.worldpop.org/geodata/summary?id=18642
[7]: https://dhsprogram.com/methodology/survey/survey-display-311.cfm

