# Mapping Health Insurance and Disability Rates for Adults in the United States
1. Using R, I mapped health insurance and disability rates by county within the United States for adults between 19-35 in 2018.

2. I utilized R librarys such as tidyverse, sf, tmap, and tmaptools. 

3. I found spatial and tabular data collected by the American Community Survey from 2012, 2014, 2016, and 2018. The spatial data includes an outline of all the counties in the United States, while the tabular data includes various statistics. I chose to focus on health insurance and disability.

4. I transformed population counts into a percentage, which is a more informative statistic in relation to my goal. 

5. To find the percentage of counties that have health insurance, I created a new column/variable for the percentage of 19 to 34-year-olds without health insurance. To do this, I divided the count of 19 to 34-year-olds with no health insurance (ins_non) by the total population aged 19-34 (in_1934) and multiplied by 100. I assigned the resulting vector of values to a new variable in 'table' called pct_uninsured.
I did this with the command below: 

<code> table$pct_uninsured <- (table$ins_non / table$in_1934) * 100 </code> 
  
6. Before creating my map, I joined my spatial and tablular data to include geometry and neccessary statistics. 
I did this with the command below:
  
<code> map_dat <- left_join(geo_dat, uninsured, by = c("GEOID", "NAME")) </code> 
  
7. Finally, I designed my own map to show health insurance and disability rates by county within the United States for adults between 19-35 in 2018 using the code below:
  
<code> 
my_map <- tm_shape(map_dat) +
  tm_fill(col = "2018", style = "cont",
    title = "% of population", ) + # set legend title
  tm_borders(lwd = 0.3, alpha = 0.5) + # add borders with width of 0.3 and 50%
  opacity
  tm_layout(
    title = "Adults aged 19-35 without health insurance by county\n (American
    Community Survey, 2018)", # "\n" inserted a line break
    title.size = 1.5, # bigger title
    title.fontfamily = "serif", # title font
    main.title = "Meleake's Adjusted Map", # add a title for the whole figure
    main.title.fontface = "bold", # make this bold
    inner.margins = c(0.05, 0.05, 0.2, 0.2), # wider margin on top and right
    side
    legend.position = c(0.8, 0.05), # x and y coordinates for legend
  ) +
  state.borders # add the state.borders layer I created earlier 
</code> 


8. I used the same process for mapping the percent of 19 to 35 year olds who are disabled in the United States in 2018. 
  
![image](https://user-images.githubusercontent.com/77419851/209524890-9ae6d118-4b7b-4c5e-81b5-3d6e27fd45df.png) 
  
![image](https://user-images.githubusercontent.com/77419851/209524906-b8648e10-3860-4cf8-b143-303370e139d7.png)
