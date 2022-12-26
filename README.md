# Using R to map insurance and disability rates by county within the United States for adults between 19-35. 


1. I utilized R librarys such as tidyverse, sf, tmap, and tmaptools. 

2. I found spatial and tabluar data collected by the American Community Survery from 2012, 2014, 2016, and 2018. The spatial data has an outline of all the counties in the United States. The tabular data includes statistics about health insurance and disability. 

3. I transformed population counts into a percentage, which is a more informative statistic in relation to my goal. 

4. To find percentage of counties that have health insurance I created a new column/variable for the percent of 19 to 34-year-olds without health insurance. To do this, I divided the count of 19 to 34-year-olds with no health insurance (ins_non) by the total population aged 19-34 (in_1934) and multiplied by 100. I assigned the resultant vector of values to a new variable in ‘table’ called pct_uninsured. 
I did this with the command below: 

<code> table$pct_uninsured <- (table$ins_non / table$in_1934) * 100 </code> 
  
  
<sub> 5. Before creating my map I joined my spatial and tablular data to include geometry and neccessary statistics. 
I did this with the command below: <sub>
  
<code> map_dat <- left_join(geo_dat, uninsured, by = c("GEOID", "NAME")) </code> 
  
7. I used the same process for finding the percent of 19 to 35 year olds who are disabled. 
  

  
  
![image](https://user-images.githubusercontent.com/77419851/209524890-9ae6d118-4b7b-4c5e-81b5-3d6e27fd45df.png) 
  
![image](https://user-images.githubusercontent.com/77419851/209524906-b8648e10-3860-4cf8-b143-303370e139d7.png)
