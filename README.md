# School_District_Analysis

##  Purpose

As a result of finding out that the reading and math grades from Thomas High School ninth graders have been altered, we are tasked with replacing the data with NaNs.  By replacing the 9th grader grades at Thomas High School with NaNs, we will have to repeat our school district analysis that we had originally ran on all of the schools in the disrict so that we can get an updated metrics that does not include the compromised school grades.


## Results

How is the district summary affected?

Once we updated our code and removed the values for the compromised 9th grader scores, it barely affects our district summary.  In our original district summary, we had the following results:

![Screen Shot 2021-11-07 at 1 46 40 AM](https://user-images.githubusercontent.com/87248687/140635344-ceaccfdb-4c1d-4d4d-8cb6-ccfb23c6d835.png)


When we run our code with the clean data, oue results are almost identical to the original district summary.

![Screen Shot 2021-11-07 at 1 48 35 AM](https://user-images.githubusercontent.com/87248687/140635380-b53c8b46-b859-4f7f-9168-42394cd54cd4.png)


How is the school summary affected?

So when we first run our code for the school summary, we got the following results.  The Thomas High School results are pretty skewed since they are calculating the average based on the counts of the school name in the dataframe.  This also ends up counting the school name for the 9th grade students with the NaNs, which gives us a much lower average.  

``` 
# Calculate the total student count.
per_school_counts = school_data_complete_df["school_name"].value_counts()
```

<img width="1094" alt="Screen Shot 2021-11-07 at 11 45 07 PM" src="https://user-images.githubusercontent.com/87248687/140685877-9bf6653d-608a-4da7-a8f6-82ea86785928.png">


When we update our data frame, to only include the grades from the 10th-12th grade at Thomas High School, once again, we see very marginal changes to the overall school's statistics.  Since this particular data frame is not formatted to the tenths decimal place, you can see the marginal differences between the results with and without the 9th grade student scores.  Here's the code we used to calculate the new student total as well as the correct averages.

```
ths_tenth_grade=school_data_complete_df[(school_data_complete_df["grade"]=="10th")& 
                                                 (school_data_complete_df["school_name"]=="Thomas High School")]
ths_tenth_grade_count=ths_tenth_grade["Student ID"].count()

ths_eleventh_grade=school_data_complete_df[(school_data_complete_df["grade"]=="11th")& 
                                                 (school_data_complete_df["school_name"]=="Thomas High School")]
ths_eleventh_grade_count=ths_eleventh_grade["Student ID"].count()
ths_twelth_grade=school_data_complete_df[(school_data_complete_df["school_name"]=="Thomas High School")&
                                                  (school_data_complete_df["grade"]=="12th")]
ths_twelth_grade_count=ths_twelth_grade["Student ID"].count()

THS_10_through_12=ths_tenth_grade_count+ths_eleventh_grade_count+ths_twelth_grade_count
                                                                                                 
```

![Screen Shot 2021-11-07 at 2 04 21 AM](https://user-images.githubusercontent.com/87248687/140635786-24206dab-92cf-4a2a-886d-a21d92e9130b.png)



How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?

Before updating the student counts in the per school data frame, Thomas High School ends up being towards the bottom in terms of passing percentage.  However, once you edit the data frame to include the student counts of only the 10-12th grades, Thomas High school's still ends up as the 2nd best school in terms of overall passing percentage.  As you can see below, the only school with a better overall passing percentage is Cabrera High School.


![Screen Shot 2021-11-07 at 2 11 20 AM](https://user-images.githubusercontent.com/87248687/140635957-5cb4353e-8ef0-40ed-a9b5-ebd686e3e28c.png)


How does replacing the ninth-grade scores affect the following:


Math and reading scores by grade

When we replaced the ninth-grade scores with NaNs and add our our math scores and reading scores to dataframes that are grouped by school, they are similar to the original data frame we created with the exception that the averages for the 9th grade scores are replaced with the value NaN as shown below.


Below is the original data frames before we replaced the 9th grade scores with NaNs.




<img width="438" alt="Screen Shot 2021-11-07 at 8 20 56 PM" src="https://user-images.githubusercontent.com/87248687/140670489-ea8f40ca-8e2a-4648-849c-c46a7247763b.png">


<img width="363" alt="Screen Shot 2021-11-07 at 8 21 04 PM" src="https://user-images.githubusercontent.com/87248687/140670493-1455dcfd-3f3d-4db6-af98-29046a3079e2.png">

The updated DataFrames include the NaN for the 9th grade reading and math scores and can be found below.

<img width="364" alt="Screen Shot 2021-11-07 at 8 23 22 PM" src="https://user-images.githubusercontent.com/87248687/140670522-19be634d-0c2e-4552-8dc4-f0019eee3982.png">

<img width="426" alt="Screen Shot 2021-11-07 at 8 23 32 PM" src="https://user-images.githubusercontent.com/87248687/140670526-b7f536d2-d3d7-4ac0-ae9e-c1fee01c3c00.png">




Scores by school spending

When it comes to the school spending summary, we have another scenario where we find that the NaN's did not substantially effect the output of our spending summary.  In both summaries, we can see that the schools that spent less per student tend to have a higer overall passing percentage.

<img width="970" alt="Screen Shot 2021-11-07 at 8 35 32 PM" src="https://user-images.githubusercontent.com/87248687/140671162-5b1dd27d-e4bd-49f2-802e-577e5d91abc5.png">

<img width="1112" alt="Screen Shot 2021-11-07 at 9 00 47 PM" src="https://user-images.githubusercontent.com/87248687/140673023-ab8f2576-ebe7-49f9-8753-a864e519804d.png">


Scores by school size

When it comes to the school size summary, we also have another situation where the NaNs did not have a major effect on the output of the summary.  Since we did not replace the total count of students at Thomas High School inside of the per_school_summary_df, Thomas High School ends up being placed into the same school size bin that it was, when we originally did our analysis.  From the school size summary, we can see that the smaller sized and medium sized schools tend to have significantly high passing percentages than the larger schools.

<img width="855" alt="Screen Shot 2021-11-07 at 9 04 08 PM" src="https://user-images.githubusercontent.com/87248687/140673251-6f59f420-d5bf-4e46-87db-d7d79a6991fb.png">


<img width="1058" alt="Screen Shot 2021-11-07 at 9 05 28 PM" src="https://user-images.githubusercontent.com/87248687/140673294-d4ef94b5-7381-4273-b314-88ff01bda0a9.png">




Scores by school type


When we create a summary of the student score metrics by school type (charter vs district), we once again see that the NaN in the 9th grader scores did not significantly change the summary, especially once we format the decimal places in the numbers.  The biggest thing we can gather from looking at this summary is that the charter schools had significantly higher passing percentages than the district schools.


<img width="1019" alt="Screen Shot 2021-11-07 at 9 06 22 PM" src="https://user-images.githubusercontent.com/87248687/140673368-a39ed67c-e015-4909-85cc-64a96d27d541.png">


<img width="916" alt="Screen Shot 2021-11-07 at 9 06 58 PM" src="https://user-images.githubusercontent.com/87248687/140673392-0fcfd795-69df-4a6e-8f20-bb851a2721f0.png">


## Summary

In short, when we updated our school_data_complete_df we located the compromised data (Thomas High School 9th grader scores) and replaced their scores with NaN's.  Once we got to our, per_school_summary_df, we realized that the NAN's drastically decreased the values for Thomas High School.  As a result, we had to calculate the student total that didn't include the 9th graders at Thomas High School so that we could get an accurate calculation of the averages.  This allowed us to conduct our analysis without compromised scores and get an accurate indicator of school metrics.

Here are the 4 takeaways we can take from this second school district analysis

  1. When we properly update our dataframe to not include the 9th grade students when calculating the school performance metrics, there is extremely marginal change between the metrics in the original analysis and the metrics in the second analysis.
  2. Once we update our per_school_summary_df with the correct data, we also find that Thomas High School remains as a top 2 school in terms of passing percentage.
  3. When we create a summary of the metrics at the grade level, we end up getting only NaN's for the 9th graders at Thomas High School.
  4. Finally, since the changes in the metrics are so marginal with the exclusion of the Thomas High School 9th grade scores, it has little to no effect on the other summaries such as the size summary, spending summary, and school type summary.




