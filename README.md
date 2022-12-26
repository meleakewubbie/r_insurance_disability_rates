# Using R to map insurance and disability rates by county within the United States for adults between 19-35 in 2018. 


1. I utilized R librarys such as tidyverse, sf, tmap, and tmaptools. 

2. I found spatial and tabluar data collected by the American Community Survery from 2018. The spatial data has an outline of all the counties in the United States. The tabular data includes statistics about health insurance and disability. 

3. I transformed population counts into a percentage, which is a more informative statistic in relation to my goal. 

4. To find percentage of counties that have health insurance I created a new column/variable for the percent of 19 to 34-year-olds without health insurance. To do this, I divided the count of 19 to 34-year-olds with no health insurance (ins_non) by the total population aged 19-34 (in_1934) and multiplied by 100. I assigned the resultant vector of values to a new variable in ‘table’ called pct_uninsured. 
I did this with the command below: 

<code> table$pct_uninsured <- (table$ins_non / table$in_1934) * 100 </code> 
  
5. Before creating my map I joined my spatial and tablular data to include geometry and neccessary statistics. 
I did this with the command below:
  
<code> map_dat <- left_join(geo_dat, uninsured, by = c("GEOID", "NAME")) </code> 
  
6. Finally, I designed my own map to show health insurance and disability rates by county within the United States for adults between 19-35 in 2018 using the code below:
  
<code> 
my_map <- tm_shape(map_dat) +
  tm_fill(col = "2018", style = "cont",
    title = "% of population", ) + # set legend title
  tm_borders(lwd = 0.3, alpha = 0.5) + # added borders with width of 0.3 and 50%
  opacity
  tm_layout(
    title = "Adults aged 19-35 without health insurance by county\n (American
    Community Survey, 2018)", # "\n" inserted a line break
    title.size = 1.5, # bigger title
    title.fontfamily = "serif", # title font
    main.title = "Meleake's Adjusted Map", # added a title for the whole figure
    main.title.fontface = "bold", # make this bold
    inner.margins = c(0.05, 0.05, 0.2, 0.2), # wider margin on top and right
    side
    legend.position = c(0.8, 0.05), # x and y coordinates for legend
  ) +
  state.borders # added the state.borders layer I created earlier 
</code> 

7. I used the same process for mapping the percent of 19 to 35 year olds who are disabled. 
  
![image](https://user-images.githubusercontent.com/77419851/209524890-9ae6d118-4b7b-4c5e-81b5-3d6e27fd45df.png) 
  
![image](https://user-images.githubusercontent.com/77419851/209524906-b8648e10-3860-4cf8-b143-303370e139d7.png)
