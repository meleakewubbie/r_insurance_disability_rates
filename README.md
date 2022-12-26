# Using R to map insurance and disability rates by county within the United States for adults between 19-35. 

1. I utilized R librarys such as tidyverse, sf, tmap, and tmaptools.
2. I found data from the American Community Survery from 2012, 2014, 2016, and 2018. 
3. I transformed population counts into more informative statistics. 
4. I created a new column/variable for the percent of 19 to 34-year-olds without health insurance. To do this, I divided the count of 19 to 34-year-olds with no health insurance (ins_non) by the total population aged 19-34 (in_1934) and multiplied by 100. I assigned the resultant vector of values to a new variable in ‘table’ called pct_uninsured. I did this with the command below: 

<code> table$pct_uninsured <- (table$ins_non / table$in_1934) * 100 <code>





![image](https://user-images.githubusercontent.com/77419851/209524890-9ae6d118-4b7b-4c5e-81b5-3d6e27fd45df.png)

![image](https://user-images.githubusercontent.com/77419851/209524906-b8648e10-3860-4cf8-b143-303370e139d7.png)
