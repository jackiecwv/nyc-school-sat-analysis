# Exploring NYC Public School SAT Results: Findings Summary

### By: Jackie CW Vescio

*Based on a guided data science project using a `schools.csv` dataset. All code and written findings are my own.*

## Purpose

This project explores New York City public school SAT standardized test scores in reading, math, and writing. The SAT is a standardized test with reading, math and writing sections intended to measure literacy, numeracy, and writing skills. These tests are quite important to students and colleges since they play a pivotal role in the admissions process.

Analyzing the performance of the NYC schools is important for a variety of stakeholders, including policy and education professionals, researchers, government, and parents considering which school their children should attend.

## The Data

The dataset I used for the project is called `schools.csv`. The dataset covers 375 schools encompassing 5 NYC boroughs (Bronx, Brooklyn, Manhattan, Queens, Staten Island). The total columns (including calculated ones) I used for the project are: `school_name`, `borough`, `average_math`, `average_reading`, `average_writing`, `total_SAT`, `num_schools` (calculated), `average_SAT` (calculated), `std_SAT` (calculated).

When the data was initially checked, there were 7 columns total. There was data missing in 20 rows of the dataset for the `percent_tested` column. I did not need this column for the calculations in this project.

**Note on the data files:** The real dataset (`schools.csv`) is not included in this repository. The analysis is based on a guided course project on NYC public school SAT results. The folder `sample_data/` contains `schools_sample.csv`, a small synthetic dataset with made-up schools and the same columns, so the code can be run. Its results will not match the findings below. To run the notebook on it, change the filename in the `pd.read_csv(...)` line.

## Findings

### Best Math Schools

Ten schools met the "best in math" cutoff, an average math score of at least 640, which is 80% of the maximum score of 800. Stuyvesant High School in the Manhattan borough was at the top of the list with an average math score of 754. Eleanor Roosevelt High School in the Manhattan borough was at the bottom of the list with an average math score of 641. The majority of the top schools appear to be science and technology focused, judging by their names. This observation is judged by name only. The data itself does not say what each school teaches.

### Top 10 Schools by Combined SAT Score

The number one high school in the "top 10 schools by combined SAT score" is again Stuyvesant High School with a combined total SAT score of 2144. Stuyvesant is 103 points ahead of the next two schools, Staten Island Technical High School and Bronx High School of Science, which tied at 2041.

Nine of the ten schools appear on both lists, including Stuyvesant at the top of each. The only differences are New Explorations into Science, Technology and Math (math list only) and Bard High School Early College (combined list only). Math is one of the three sections in the total, so some overlap is expected.

### Borough With the Largest Standard Deviation

Manhattan had the largest spread in combined SAT scores, with a standard deviation of about 230.

Standard deviation shows how spread out school scores are from their borough's average. A larger standard deviation means scores vary more; a smaller one means they're more clustered around the average.

Manhattan's average combined SAT score is about 1340, with a standard deviation of about 230, so its scores are more spread out than the Bronx's, whose average is about 1203 and standard deviation of about 150. Manhattan has the largest standard deviation, but it is only 8 points higher than Staten Island's 222. Since Staten Island has just 10 schools compared with Manhattan's 89, that estimate is based on a much smaller group and may be less representative.

## Limitations

These results describe school averages, not individual student averages. A school's average can hide big differences inside the school and it can't tell us how any individual student did.

Staten Island has only 10 schools, so its standard deviation of about 222 comes from a very small group. One unusually high-scoring school, Staten Island Technical High School, accounts for most of that spread, so the close gap with Manhattan should be read with caution. As a check, I filtered the Staten Island rows, removed Staten Island Technical High School, and took the standard deviation of `total_SAT` again. With that one school, Staten Island's standard deviation is about 222. Without it, the number drops to about 73. So the spread that nearly ties Manhattan comes mostly from one school.

I did not use the column `percent_tested`, which was missing for 20 schools. That could matter because not all students take the SAT. In my check, the top 10 schools all had a high share tested (about 71% to 100%), while the typical school had about 65% participation. So, who takes the test may affect the averages.

Also, I must point out that the dataset has no "year" column, so it appears to cover a single year of test scores. To do a more thoughtful comparison, it would be better to have several years of data.

## Possible Next Steps

If I had more time, I would investigate these items further to acquire a better understanding of the performance differences between the top and bottom performing schools.

- I would check whether the share of students tested (`percent_tested`) relates to scores.
- Brooklyn has the most schools (109) but only one in the top 10. I would investigate if that pattern is real, and whether it holds when I look beyond the top 10 schools.
