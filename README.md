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

So when we originally ran our code for the school summary, we got the following results.


![Screen Shot 2021-11-07 at 1 56 46 AM](https://user-images.githubusercontent.com/87248687/140635595-67239b3a-2845-475b-b000-a1662f558897.png)

When we update our data frame, to only include the grades from the 10th-12th grade at Thomas High School, once again, we see very marginal changes to the overall school's statistics.  Since this particular data frame is not formatted to the tenths decimal place, you can see the marginal differences between the results with and without the 9th grade student scores.


![Screen Shot 2021-11-07 at 2 04 21 AM](https://user-images.githubusercontent.com/87248687/140635786-24206dab-92cf-4a2a-886d-a21d92e9130b.png)



How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?

Even when you replace Thomas High school's ninth grade math and reading scores with NaN's, they still end up as the 2nd best school in terms of overall passing percentage.  As you can see below, the only school with a better overall passing percentage is Cabrera High School.


![Screen Shot 2021-11-07 at 2 11 20 AM](https://user-images.githubusercontent.com/87248687/140635957-5cb4353e-8ef0-40ed-a9b5-ebd686e3e28c.png)


## Summary
