# STAR Project Analysis : The Effect of Class Sizing on First Grade Students Math Performance
STAR Project Analysis

Project Title: The Effect of Class Sizing on First Grade Students Math Performance

Author : Feini Pek

What the project does:
This investigation addressed two primary questions regarding the influence of various class types, categorized by size, on the mathematical performance of grade 1 students: (a) whether differences exist in math scaled scores among 1st-grade students across different class types, and (b) which class type correlates with the highest math scaled scores among 1st-grade students. The study included 6,829 students who participated in Tennessee's class-size initiative, Project STAR, during their first grade. Upon inspecting the dataset, patterns of missing data were observed, and addressed through data imputation in variables of interest. An issue of heterogeneity also surfaced as student race and socioeconomic status (SES) were unevenly distributed across various school types. This was accounted for by incorporating race and free-lunch variables in the analysis. Additionally, noncompliance emerged as a challenge, with actual class sizes often diverging from their assigned class types. To mitigate this, the variable representing class type was substituted with variables representing true class size in sensitivity analysis. The outcomes consistently revealed the existence of differences in scaled math scores among different class sizes, with small classes consistently demonstrating the highest mean math scores across all models.

---------------------------------------------------------------------------------------------------------

Why the project is useful:
Studying whether differences exist in math scores among first-grade students across different class types and determining which class type correlates with the highest math scores is valuable for several reasons:

1). Informed Decision-Making: 
Provides insights for educators, policymakers, and administrators to make informed decisions about resource allocation, curriculum development, and instructional strategies.

2). Improving Educational Practices: 
Helps educators identify effective instructional practices and classroom environments that promote academic achievement.

3). Policy Development: Guides the development of educational policies aimed at improving student achievement and supporting academic success for all students.

---------------------------------------------------------------------------------------------------------

Dataset Information :
- Dataset Title : Tennessee's Student Teacher Achievement Ratio (STAR) project
- Source: https://dataverse.harvard.edu/dataverse/star
- Data used from the set : STAR_K-3_Schools.sav
- Dataser guide : starUsersGuide.pdf
- Dataset size: 11601 rows x 379 variables

Variable of interest:
- g1tmathss : scaled math score for grade 1 students
- g1classtype : class type assigned (1 = Small, 2 = Regular, 3 = Regular + Aide)
- g1classsize : class size (e.g. 17, 21, 25)
- g1schid : unique six digits for each school, the first three digits indicating the district code
- g1tchid : unique ID for each teacher
- race : students' race (1 = White, 2 = Black, 3 = Asian, 4 = Hispanic, 5 = Native American, 6 = Others)
- g1freelunch : students' free lunch status (1 = Yes, 2 = No)
- g1surban : urbanicity of school location (1 = Inner-city,  2 = Suburban, 3 = Rural, 4 = Urban)

---------------------------------------------------------------------------------------------------------

Analysis File Information:
Format: R markdown

---------------------------------------------------------------------------------------------------------

Getting Started:
To get started with the analysis

1). Install R and RStudio:If you haven't already, download and install R from CRAN and RStudio. RStudio provides an integrated development environment (IDE) for working with R, making it easier to write and execute code. (Find how to here: https://rstudio-education.github.io/hopr/starting.html)
Once installed, open RStudio

2). Install Required Packages: In RStudio, open the R script or R Markdown document where the analysis will be conducted. Install any required R packages by running the following command: install.packages("package_name")
The following packages are used in this analysis:
- Data Manipulation and Analysis: dplyr, tidyr, haven
- Visualization: ggplot2, ggpubr, gplots, cowplot, RColorBrewer
- Statistical Modeling and Analysis: AER, car
- Numerical Computation: pracma
- Report Generation and Output:knitr, DT

3). Load the Data: Load the Project STAR data into your R environment. For .sav file, can use the following command:
    read_sav("dataverse_files/STAR_Students.sav")
    For more information on how to import different data type: https://www.datacamp.com/tutorial/r-data-import-tutorial

4). Explore the Data: Once the data is loaded, take some time to explore its structure, variables, and summary statistics.
    Some functions used for exploration : summary(), table()

---------------------------------------------------------------------------------------------------------

Analysis Overview:
Our analysis aims to address the question of whether there are differences in math scores between different class types and to identify which class type is associated with the highest math score. The main variables considered in our analysis are scaled math score, class type, and school ID.

Caveats: We identified missing data and encountered issues with heterogeneity and noncompliance. These challenges were addressed through data imputation, additional variable inclusion (race and free lunch), and variable substitution (class size and school urbanicity) respectively.

Descriptive analysis: imputation had minimal impact on the variables of interest (through visualizations of imputed variable before and after imputation). Examining the relationship between class size and math scores, differences in math scores was observed between different class types, with small classes having the highest median scores. Additionally, variations in math scores across different schools were observed, with some schools scoring well above the average of small classes and others below the average of regular classes.

Inference analysis: we opted to utilize a multiple linear regression model. The data were aggregated based on teacher ID to obtain each class as an observation, with math score as the response variable and class type, school ID, race, and free lunch as independent variables. Model testing revealed that additional race and free lunch variables were not significant and were subsequently dropped from the model. We proceeded with a model using only class type and school ID as predictors. 

Model diagnostic: Model diagnostic tests indicated no significant errors, ensuring the eligibility of the model. 

Sensitivity analysis: To test the sensitivity of the model, three analyses were conducted: complete case analysis, substitution of school urbanicity for school ID, and replacement of class type with actual size.

Secondary question: Tukey's Honest Significant Difference (HSD) test was performed to compare the mean math score of each combination of class type

Throughout the analysis and model fitting process, the results consistently pointed to differences in math scores across different class types, with small classes consistently exhibiting the highest mean scores. This led us to conclude that small class type is associated with the highest math scores.

---------------------------------------------------------------------------------------------------------

Limitations and Challenges:

Despite our thorough analysis, several limitations and challenges were encountered during the process. One notable limitation was the need to address missing data, heterogeneity, and noncompliance, which required extensive data imputation, variable inclusion, and substitution. While these techniques helped mitigate potential biases, they may have introduced uncertainties in the analysis results.

Additionally, the decision to prioritize interpretability over minor deviations from normality in the regression model could pose risks to the validity of the analysis. While this approach may offer clarity in interpretation, it may overlook significant deviations from normality that could impact the accuracy of inferential procedures. Future analyses should carefully consider the balance between interpretability and adherence to statistical assumptions to ensure robust and reliable results.

---------------------------------------------------------------------------------------------------------

Appendix:
- star : original dataset with 11601 observations and 379 variables
- star2 : dataset with 11601 observations and 34 variables corresponding to grade 1 information
- star_na : dataset after NA removal (6829 rows, 34 variables)
- imp_data : data with imputed values for race, free lunch, and math scores
- agg_data : dataset containing aggregated imp_data based on school id,
             where the math score became the mean math score, and each observation is a classroom
- in_star : dataset of students who are in STAR in grade 1
- not_in : dataset of students who are not in STAR in grade 1
- data_with_1 :  dataset of students who spent 1 year in STAR project
- data_with_2 : dataset of students who spent 2 year in STAR project
- data_with_3 : dataset of students who spent 3 year in STAR project
- no_return : dataset of students who did not continue in STAR after kindergarten
- return : dataset of students who continued in STAR after kindergarten
- male : dataset containing male students in star in grade 1
- female : dataset containing female students in star in grade 1
- white : dataset containing white students in star in grade 1
- black : dataset containing black students in star in grade 1
- asian : dataset containing asian students in star in grade 1
- hispanic : dataset containing hispanic students in star in grade 1
- native : dataset containing native american students in star in grade 1
- other : dataset containing students who identify as other race in star in grade 1
- inner : dataset containing students who went to inner-city schools in star in grade 1
- suburb : dataset containing students who went to suburb schools in star in grade 1
- rural : dataset containing students who went to rural schools in star in grade 1
- urban : dataset containing students who went to urban schools in star in grade 1
- class1 : dataset containing students in small classes in star in grade 1
- class2 : dataset containing students in regular classes in star in grade 1
- class3 : dataset containing students in regular + aide classes in star in grade 1
- small1 : dataset containing students in small classes in star in grade 1 (from imputed data)
- reg1 : dataset containing students in regular classes in star in grade 1 (from imputed data)
- regaid1 : dataset containing students in regular + aide classes in star in grade 1 (from imputed data)
- small2 : dataset containing students in small classes in star in grade 1 (from aggregated data)
- reg2 : dataset containing students in regular classes in star in grade 1 (from aggregated data)
- regaid2 : dataset containing students in regular + aide classes in star in grade 1 (from aggregated data)

Models:
- n_model : model with classtype, schoolid, race, and freelunch as predictor
- n_model2 : model with classtype, schoolid as predictor
- n_model_log : model with classtype, schoolid as predictor and log math score as response
- cc_model : model with classtype, schoolid as predictor, using non imputed dataset
- model3 : model with classtype, school urbanicity as predictor
- model4 : model with class size, schoolid as predictor

---------------------------------------------------------------------------------------------------------

References:

CES Academy. 4 REASONS WHY SMALL CLASS SIZES LEAD TO BETTER STUDENT PERFORMANCE. https://www.ces-schools.net/4-reasons-why-small-class-sizes-lead-to-better-student-performance/#:~:text=With%20a%20smaller%20class%20size,maneuver%20and%20more%20personal%20space.

Chen, Shinze.Chapter 4 Analysis of Variance. https://nbviewer.org/github/ChenShizhe/StatDataScience/blob/master/Notes/Chapter4ANOVAII.ipynb

C.M. Achilles; Helen Pate Bain; Fred Bellott; Jayne Boyd-Zaharias; Jeremy Finn; John Folger; John Johnston; Elizabeth Word, 2008, “Tennessee’s Student Teacher Achievement Ratio (STAR) project”, https://doi.org/10.7910/DVN/SIWH9F, Harvard Dataverse, V1, UNF:3:Ji2Q+9HCCZAbw3csOdMNdA== [fileUNF]

Dynarski, Susan., & Hyman, Joshua (2013). Experimental Evidence on the Effect of Childhood Investments on Postsecondary Attainment and Degree Completion. Journal of Policy Analysis and Management 32(4). https://www.researchgate.net/publication/228303207_Experimental_Evidence_on_the_Effect_of_Childhood_Investments_on_Postsecondary_Attainment_and_Degree_Completion

Finn, J.D., Gerber, S.B. (2005). Small Classes in the Early Grades, Academic Achievement, and Graduating From High School. Journal of Educational Psychology2005, Vol. 97, No. 2, 214–223.

Gerbing,David. Subset a Data Frame. https://cran.r-project.org/web/packages/lessR/vignettes/Extract.html#:~:text=If%20subsetting%20is%20done%20by,%2C%20d%5B%2Ccols%5D%20.

Hadley,Wickham, et al., A box and whiskers plot (in the style of Tukey). ggplot2. https://ggplot2.tidyverse.org/reference/geom_boxplot.html

Kassambara, Alboukadel. Data Manipulation in R. Data Novia. https://www.datanovia.com/en/lessons/select-data-frame-columns-in-r/

Keyes,David.(2022, March 12). How to Make Beautiful Tables in R. R for the rest of us. https://rfortherestofus.com/2019/11/how-to-make-beautiful-tables-in-r

Krueger, A. B., & Whitmore, D. M. (2001). The Effect of Attending a Small Class in the Early Grades on College-Test Taking and Middle School Test Results: Evidence from Project STAR. The Economic Journal, 111(468), 1–28. http://www.jstor.org/stable/2667840

Lane, D. (2010). Tukey’s honestly significant difference (hsd). In Encyclopedia of Research Design (Vol. 0, pp. 1566-1570). SAGE Publications, Inc., https://doi.org/10.4135/9781412961288

National Center for Education Statistics. Status and Trends in the Education of Racial and Ethnic Minorities. https://nces.ed.gov/pubs2010/2010015/tables/table_1a.asp

Statistical tools for high-throughput data analysis. (n.d.) Normality Test in R. https://owl.purdue.edu/owl/research_and_citation/apa_style/apa_formatting_and_style_guide/reference_list_electronic_sources.html

Toth, Michael. (May 1, 2019). Detailed Guide to the Bar Chart in R with ggplot. R-bloggers. https://www.r-bloggers.com/2019/05/detailed-guide-to-the-bar-chart-in-r-with-ggplot/


