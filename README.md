# Conjoint-Analysis

# Choice based Conjoint Analysis on Wine Preference of Italian Consumers

***Abstract***  - **This project aims to conduct a random survey design for collecting responses regarding wine preferences of Italian consumers. Furthermore, it attempts to understand how preference share gets affected as we vary different attributes associated with wine.**

***Keywords***  - Conjoint Analysis, part worth estimate, mlogit, customer heterogeneity, random design

#### **Introduction**

Wine Industry in Italy takes one of the leading places in the local economy. Furthermore, Italy is the world-leading wine-producing country both in terms of volume and exports. There are more than 100 wine brands from more than 20 regions across Italy. In the previous studies dedicated to wine consumer behavior, the main criteria for customers to evaluate and purchase wine are based on price, awards, region, the taste of wine or even personal recommendations. Researchers also found some differences in respondents' preferences according to age, involvement level, and the geographical part they were from. The research method we used, called Conjoint Analysis, is designed on the view that consumers' values are based on the utility offered by products' attributes. Our study involves a series of interrelated stages which can be classified into 4 main steps. The first step in conducting the analysis is to identify suitable attributes and levels as motivators for consumer choice & conducting the survey based on the design chosen. The second is to perform data pre-processing and exploratory analysis on the collected data. Thirdly, we had to implement the Multinomial Choice model with Conditional Logistic Regression. The fourth & the last step is to implement the Multinomial Choice model but taking into account the customer heterogeneity as well. With these, further preference shares can be derived.

***Note for the reader***: Please refer to the original report shared in PDF [here](https://github.com/KSwaviman/Conjoint-Analysis/blob/main/A%20Study%20on%20The%20Wine%20Preference%20of%20Italian%20Consumers%20Report.pdf) for better understanding. The following text is a converted markdown of the same PDF which may have improper formatting and missing image files. Link to the original study [*here*](https://github.com/KSwaviman/Conjoint-Analysis/blob/main/A%20Study%20on%20The%20Wine%20Preference%20of%20Italian%20Consumers%20Report.pdf).

#### **Problem definition: purpose of study**

This project aims to investigate the choice-making process and preferences for wine among customers in Trento. In particular, the main goal is to determine how customers value different features of the wine and find the optimal levels of product attributes that maximize sales. Moreover, this project helps to answer questions about more popular types of wine among youth, providing information about the segmentation of customers and brands positioning. At the core of the project is conjoint analysis – a survey-based statistical technique, which allows to perform market research and estimate market share for products or services. The chosen method of the project is a choice-based conjoint survey, subsequently analyzed by using generalized linear models. Methods of conjoint analysis yield estimates of attribute trade-offs using a formal model for analysis.


#### **Design of Conjoint Survey**

The basic principles of designing a conjoint survey involve four different steps, such as determination of the type of study, identifying the relevant attributes, specifying the attributes' levels and designing a questionnaire.

As regards the former step, it has been conducted a branded choice-based conjoint survey, where customers are asked to choose from several alternatives of the product profiles.

Considering the study design, it has selected the salient attributes and levels for constructing the hypothetical product profiles of wine. Since attributes of a product can be divided broadly into categorical (nominal, ordinal, binary) and quantitative classes, in our study it has been used 5 attributes in total of both types. Particularly, nominal quantitative attributes of the survey include price, aging time of wine and percentage of alcohol, while categorical attributes involve brand and type of wine. Each attribute occurs at some level, therefore, it has been chosen from 4 to 5 levels for the attributes, based on the understanding of the consumer's choice process.

##### **3.1 Attributes and their levels:**

Price per bottle: Value (3-10€), Popular (10-15€), Premium (15-30€), Luxury (50-100€)

Brands: Cavit, Mezzacorona, Ferrari, Cantina Toblino

Type of wine: red wine, white wine, sparkling wine, rose wine.

Alcohol Percentage: 5.5%, 7%, 12%, 18%

Wine aging time: 1 year, 2 years, 3 years, 4 years, 5 years

In order to collect data for the conjoint analysis, the choice-based conjoint survey was conducted. The designed survey consists of 7 questions with 4 alternatives for each question and the questionnaire deals with 4-5 attributes with each level. As a result, each respondent had to evaluate a total number of 7 × 4 = 28 product profiles. To cover more combinations, it has been chosen random design of the conjoint survey, Thus, from 4× 4 × 4 × 4 × 5 = 1280 combinations in total, the questionnaires cover 840 combinations of product profiles. Considering time and source limitations in conducting the survey, the determined sample size of the survey is 30 respondents in total. The respondents were asked to choose one out of 4 product profiles of wine, which they are more likely to buy.

For example, the choice between four bottles of wine with different characteristics:

-Option 1: A bottle of sparkling wine from Cantina Toblino brand in popular price segment (10-15 euros) with 12% of alcohol and 3 years of aging

-Option 2: A bottle of white wine from Ferrari brand in value price segment (3-10 euros) with 7% of alcohol and 2 years of aging

-Option 3: A bottle of sparkling wine from Ferrari brand in value popular price segment (10-15 euros) with 7% of alcohol and 2 years of aging

-Option 4: A bottle of rose wine from Mezzacorona brand in value popular price segment (10-15 euros) with 12% of alcohol and 5 years of aging

![](RackMultipart20230204-1-4ijigk_html_47aa00450be9de4d.png)

Fig.1 Example of a question in the conjoint survey

Moreover, in addition to the choice-based conjoint questions, social-demographic data of the respondents, such as age, gender, level of education, employment status, ethnicity, usage of social media platforms and level of daily physical activity was collected.


#### **Exploratory Data Analysis**

It is important to analyze basic descriptive statistics of the collected data set to understand its initial features and summarize the main characteristics. Descriptive statistics also help to understand if there are any imbalances as well as missing values in the data. Firstly, we analyzed the descriptive social-demographic statistics of the respondents.

![](RackMultipart20230204-1-4ijigk_html_98026b81d2a8267a.png)

Fig.2 Respondents distribution by gender

Female respondents represent 43% of the total number of respondents, while male respondents represent around 57% of the total.

![](RackMultipart20230204-1-4ijigk_html_8d80dfbe0c1015a.png)

Fig.3 Respondents distribution by age

The vast majority of the respondents belong to the age group of 18 to 29 years. The remaining participants are included in the following groups: 30-40 years old-7% of the respondents; 60+ years old-3% of the respondents.

![](RackMultipart20230204-1-4ijigk_html_a568d07ab3654cce.png)

Fig. 4 Respondents distribution by ethnicity

The graph indicates that more than 45% of respondents are Italians, while other nationalities spread in the proportion of 3% and 7%.

![](RackMultipart20230204-1-4ijigk_html_55eeb60654b6a7a5.png)

Fig.5 Percentage of Social Platforms used by respondents

The most popular Social Platform used by 46% of respondents is Instagram, followed by Facebook, Linkedin, and Twitter with 22% and 14% of respondents respectively **.**

Summarizing the collected data of the choices by respondents, we estimated that the most preferred attributes among price segments and brands are Ferrari and Popular (10-15€) price segments.

![](RackMultipart20230204-1-4ijigk_html_50e3b8dcc704a23d.png)

Fig.6Choice distribution by brand and by price

![](RackMultipart20230204-1-4ijigk_html_364a6c5cc9bb5227.png)

Fig. 7 Choice distribution by type of wine and by aging time

In addition, it is noticeable that when evaluating white wine options, respondents prefer Mezzacorona and Cavit brands the most, whereas for other types of wine the most widely chosen brand is Ferrari.

![](RackMultipart20230204-1-4ijigk_html_7e46edbf3f67d96f.png)

Fig.8 Choice distribution by type of wine, brand, and price

![](RackMultipart20230204-1-4ijigk_html_bf4168fc38356685.png)

Fig.8Percentage of respondents distribution by brand and price

Moreover, if we consider the distribution of chosen brands among 4 price segments, in Value (3-10€) price segment the two leading brands among respondents are Ferrari and Mezzacorona, in Popular (10-15€) segment the most popular brands are Ferrari and Cavit. Nevertheless, in the Premium(15-30€) segment Mezzacorona is taking the leading place, followed by Cavit.

![](RackMultipart20230204-1-4ijigk_html_6ec0b6404b9bd7fb.png)

Fig.9Number of respondents by brand and physical activities

The following chart represents the chosen brands and the level of physical activities of the respondents. Overall, the distribution of physical activities spread equally, nonetheless, Cavit has the lowest percentage of respondents, who do not do physical activities on a daily basis.

![](RackMultipart20230204-1-4ijigk_html_d51d04b953a169af.png)

Fig. 10 Percentage of respondents distributed by physical activities and percentage of Alcohol

Analyzing the graph, it is noticeable that respondents with a moderate and high level of physical activity prefer 7% of alcohol, while respondents with a low level of activity prefer 5.5% of alcohol.

![](RackMultipart20230204-1-4ijigk_html_6b8c3405f16af2df.png)

Fig. 11 Number of respondents by brand and Social Platforms

The graph indicates that respondents, who chose the Ferrari brand in the questionnaire, use Twitter less than the other platforms. In contrast, respondents who chose Cantina Toblino are engaged with Twitter more. Moreover, among Ferrari's choices, only a small percentage of respondents don't use any social platforms.

![](RackMultipart20230204-1-4ijigk_html_dee5d47fdc7db1e8.png)

Fig. 12 Distribution by brand and other 3 attributes


#### **Choice Model with Conditional Logistic Regression**

##### **5.1 Utility function**

Chosen forms of component utility functions are part worth function and vector models:

- preference rating given to the ith product,

- level of the price for the ith product,

- level of the brand for the ith product,

- level of the type of wine for the ith product,

- level of the alcohol percentage for the ith product,

- level of the wine aging time for the ith product,

- partworth function for attribute 1 (price),

- partworth function for attribute 2 (brand),

- partworth function for attribute 3 (type of wine),

- partworth function for attribute 4 (alcohol percentage),

- partworth function for attribute 5 (wine aging time),

In this case, the probability of choosing the alternative i is increasing with the biggest value .

Therefore, probability of choice of any alternative for the individual is equal to:

,

,

,

,

4

##### **5.2 Multinomial Logit Model**

**Model description**

Multinomial logit model is used for analyzing choice-based conjoint data. In the usual multinomial logit model, the expected utilities are modeled in terms of the characteristics of the individuals.

Utilities derived by the individual for four alternatives are:

,

where three kinds of covariates are considered:

- alternative-specific attributes with common coefficients β
- alternative-specific attributes with alternative-specific coefficients
- individual-level variables with alternative-specific coefficients

Thus, probability of choice:

,

In order to use the collected dataset in the multinomial logit model, it has been organized into the following data format:

| ~~~~~~~
 first 10 observations out of 840
 ~~~~~~~
 ques Price Brand Type.of.Wine Percentage.of.Alcohol
 1 1 Value(3€-10€) Cavit White wine 5.5 %
 2 1 Popular(10€-15€) Mezzacorona White wine 18 %
 3 1 Premium(15€-30€) Ferrari Rose wine 12 %
 4 1 Popular(10€-15€) Ferrari Rose wine 18 %
 5 2 Premium(15€-30€) Mezzacorona Sparkling wine 7 %
 6 2 Value(3€-10€) Cantina Toblino Rose wine 12 %
 7 2 Luxury(50€-100€) Ferrari Sparkling wine 12 %
 8 2 Luxury(50€-100€) Mezzacorona Red wine 7 %
 9 3 Luxury(50€-100€) Ferrari White wine 7 %
 10 3 Value(3€-10€) Cantina Toblino Sparkling wine 7 %
 Aging.time.of.Wine Choice idx
 1 3 years FALSE 1:1
 2 1 year TRUE 1:2
 3 1 year FALSE 1:3
 4 4 years FALSE 1:4
 5 4 years TRUE 2:1
 6 5 years FALSE 2:2
 7 2 years FALSE 2:3
 8 4 years FALSE 2:4
 9 1 year FALSE 3:1
 10 4 years FALSE 3:2

 ~~~indexes~~~~
 chid resp.id alt
 1 1 1 1
 2 1 1 2
 3 1 1 3
 4 1 1 4
 5 2 1 1
 6 2 1 2
 7 2 1 3
 8 2 1 4
 9 3 1 1
 10 3 1 2
 indexes: 1, 1, 2 |
| --- |

**5.3 Fitting the Multinomial Logit Model without intercepts:**

A model with only alternative specific variables is called a conditional logit model. Considering that this model does not have intercepts =0, the equation for the utilities can be simplified into:

To calculate the data, it was used the mlogit package:

| m1 \<- mlogit(Choice ~ 0 + Price + Brand + Type.of.Wine +Percentage.of.Alcohol +Aging.time.of.Wine, data = cbc.mlogit) |
| --- |

As a result, we were given the estimated part worth coefficients:

| Coefficients :
 Estimate Std. Error z-value Pr(\>|z|)
 PricePopular(10€-15€) 1.503812 0.274514 5.4781 4.299e-08 \*\*\*
 PricePremium(15€-30€) 1.034239 0.294471 3.5122 0.0004444 \*\*\*
 PriceValue(3€-10c) 1.423789 0.285615 4.9850 6.197e-07 \*\*\*
 BrandCavit 0.353767 0.250166 1.4141 0.1573237
 BrandFerrari 0.875427 0.243341 3.5975 0.0003213 \*\*\*
 BrandMezzacorona 0.663960 0.250648 2.6490 0.0080736 \*\*
 Type.of.WineRose wine -0.083027 0.254559 -0.3262 0.7443021
 Type.of.WineSparkling wine 0.217729 0.236474 0.9207 0.3571916
 Type.of.WineWhite wine 0.238447 0.241399 0.9878 0.3232645
 Percentage.of.Alcohol18 % 0.224076 0.246609 0.9086 0.3635468
 Percentage.of.Alcohol5.5 % 0.388347 0.241419 1.6086 0.1077041
 Percentage.of.Alcohol7 % 0.311218 0.239271 1.3007 0.1933633
 Aging.time.of.Wine2 years -0.437539 0.277900 -1.5744 0.1153839
 Aging.time.of.Wine3 years 0.048895 0.257447 0.1899 0.8493700
 Aging.time.of.Wine4 years -0.229575 0.275379 -0.8337 0.4044683
 Aging.time.of.Wine5 years -0.024921 0.267110 -0.0933 0.9256665
 ---
 Signif. codes: 0 '\*\*\*' 0.001 '\*\*' 0.01 '\*' 0.05 '.' 0.1 ' ' 1 |
| --- |

**The Estimate** shows the mean values for each level, which must be understood in relation to each attribute's base levels with a magnitude of preferences from -2 to 2 on the logit scale. Considering this case study, the Estimate for price is measured relative to Luxury (50-100€) price segment base level. This leads to the fact that our simulated customers strongly preferred Popular (10-15€) and then Value (3-10€) price segments to the Luxury segment. Considering The Estimate values of brands, it is noticeable that the most preferred brand is Ferrari, followed by Mezzacorona and Cavit relative to Cantina Toblino brand. Likewise, it can be estimated that the simulated customers slightly dislike Rose wine in relation to Red wine and they tend to prefer 1 and 3 years of aging time to others.

**The Std. Error** indicates the level of precision of the estimates, which is directly proportional to the size of the conjoint survey data. These coefficients mean that the value of the estimate will fall within the _estimate ±1.96× the std.error_. For example, assuming the data are representative, there is a 0.95 probability that the coefficient for price Popular (10-15€) varies between 2.02 and 0.97.

##### **5.4 Fitting the Multinomial Logit Model with intercepts:**

The second estimated model in the study case is a multinomial logit with intercepts. The equation for the utility functions is the following:

To estimate the second Multinomial Logitmodel, we used mlogit with a formula describing the model:

| m2 \<- mlogit(Choice ~ Price + Brand + Type.of.Wine +Percentage.of.Alcohol +Aging.time.of.Wine, data = cbc.mlogit) |
| --- |

As a result, the estimated part worth coefficients:

| Coefficients :
 Estimate Std. Error z-value Pr(\>|z|)
 (Intercept):2 0.270761 0.214650 1.2614 0.2071636
 (Intercept):3 0.141093 0.223449 0.6314 0.5277566
 (Intercept):4 0.389553 0.210497 1.8506 0.0642213 .
 PricePopular(10€-15€) 1.496454 0.275723 5.4274 5.719e-08 \*\*\*
 PricePremium(15€-30€) 1.011992 0.298370 3.3917 0.0006945 \*\*\*
 PriceValue(3€-10€) 1.392920 0.287908 4.8381 1.311e-06 \*\*\*
 BrandCavit 0.380192 0.253446 1.5001 0.1335906
 BrandFerrari 0.873869 0.244195 3.5786 0.0003455 \*\*\*
 BrandMezzacorona 0.696337 0.253610 2.7457 0.0060382 \*\*
 Type.of.WineRose wine -0.079270 0.256657 -0.3089 0.7574297
 Type.of.WineSparkling wine 0.246208 0.237565 1.0364 0.3000234
 Type.of.WineWhite wine 0.252377 0.243251 1.0375 0.2994950
 Percentage.of.Alcohol18 % 0.218244 0.248314 0.8789 0.3794536
 Percentage.of.Alcohol5.5 % 0.418252 0.243099 1.7205 0.0853419 .
 Percentage.of.Alcohol7 % 0.316370 0.240103 1.3176 0.1876230
 Aging.time.of.Wine2 years -0.422761 0.279153 -1.5144 0.1299138
 Aging.time.of.Wine3 years 0.045125 0.258801 0.1744 0.8615808
 Aging.time.of.Wine4 years -0.231177 0.276693 -0.8355 0.4034370
 Aging.time.of.Wine5 years -0.022488 0.267952 -0.0839 0.9331148
 ---
 Signif. codes: 0 '\*\*\*' 0.001 '\*\*' 0.01 '\*' 0.05 '.' 0.1 ' ' 1

 Log-Likelihood: -258.16
 McFadden R^2: 0.10552
 Likelihood ratio test : chisq = 60.91 (p.value = 3.6749e-07) |
| --- |

The alternative specific constantsindicate a preference for the different positions in the question (1,2,3,4) in relation to the firstposition.

| Estimate Std. Error z-value Pr(\>|z|)
 (Intercept):2 0.270761 0.214650 1.2614 0.2071636
 (Intercept):3 0.141093 0.223449 0.6314 0.5277566
 (Intercept):4 0.389553 0.210497 1.8506 0.0642213 |
| --- |

(Intercept):4 illustrates the relative preference of the fourth position in the question (versus the first), as well as (Intercept):2 and (Intercept):3 indicate the preference for the second and third positions to varying degrees relative to the first one. The estimated alternative specific constants are not significantly different from zero.

Considering the estimated values of part worth coefficients of the multinomial logit model with intercepts, there is no significant difference from the multinomial logit model without intercepts.

##### **5.5 Model Comparison:**

Once we build the multinomial logistic regression models once with intercepts included and once without considering intercepts, the next logical step is to check if adding intercepts adds any significant value to the model outcome or not. In order to test that we make use of a likelihood ratio test.

| #Df LogLik Df Chisq Pr(\>Chisq)
 \<dbl\> \<dbl\> \<dbl\> \<dbl\> \<dbl\>
 1 16 -260.0942 NA NA NA
 2 19 -258.1610 3 3.86641 0.2762554 |
| --- |

Likelihood ratio test gives a p-value of 0.27, which is way higher than the conventional threshold of 0.05. Hence, we can conclude that the two models m1 and m2 fit the data equally well. We cannot reject the null hypothesis that there is no significant difference between m1 and m2 and we don't need the alternative specific constants to fit the present data. This also means, excluding intercepts from our model doesn't affect the result significantly. Hence for further analysis, we will only consider the m1 model which excludes intercepts.

##### **5.6 Preference Shares Simulator**

With the help of a share simulator, we can specify a variety of alternatives and then use the model to anticipate which options customers will select. In our case, we analyzed preference shares for different types of wine in different price segments among different brands.

In order to create the preference shares simulator, we built a function for predicting shares from a multinomial logit model:

| predict.mnl \<- function(model, data) |
| --- |

We computed choice shares using multinomial logit model m1 without intercepts. Based on our exploratory analysis we observe that within Brand Cavit, customers prefer the Popular(10€‎-15€‎) price segment, white wine, 5.5% alcohol with 4 years of aging the most. Hence we design a combination for that which does not exist in our initial survey design. We will compare this new proposed design against various combinations of other brands, based on the most chosen attributes within each brand.

| share Price Brand Type.of.Wine Perc.of.Alcohol Aging.time.of.Wine
 \<dbl\> \<fct\> \<fct\> \<fct\> \<fct\> \<fct\>
8220.08791050 Popular(10€-15€) Cavit White wine 5.5 % 4 years
6100.09992091 Popular(10€-15€) Cantina Toblino Sparkling wine 7 % 3 years
6740.11776021 Popular(10€-15€) Cantina Toblino Sparkling wine 12 % 3 years
7380.10901894 Popular(10€-15€) Cantina Toblino Sparkling wine 18 % 3 years
3620.14743278 Popular(10€-15€) Ferrari Sparkling wine 7 % 2 years
6180.23980020 Popular(10€-15€) Ferrari Sparkling wine 7 % 3 years
6380.19815646 Popular(10€-15€) Mezzacorona White wine 7 % 3 years |
| --- |

As a result, we found that, among this set of the most popular wine profiles, we would expect 24% of consumers to choose Sparkling wine from Ferrari brand in the Popular(10€-15€) price segment with 7% of alcohol and 3 years of aging time.

##### **5.7 Trade-off Table & Sensitivity Plot:**

A trade-off table and a sensitivity plot show the relative importance of different attributes and levels in a choice model, and how changing the levels of one attribute affects the likelihood of choosing one option over another. The trade-off table shows the part-worth or utility value of each attribute level, while the sensitivity plot shows how these values change as one attribute level is changed while keeping all others constant. These tools help to understand the trade-offs that consumers make between different attributes and levels and the degree to which they are willing to compromise on one attribute to get another. They also provide insights into how consumers value different attributes and how changes to them may affect demand.

Based on the estimated preference shares, we can build a plot, representing how shares would change if we changed each of the attributes of the product profiles. This information on consumer preferences can be used to examine which product characteristics appeal to customers the most and how they trade off desirable qualities and pricing.

![](RackMultipart20230204-1-4ijigk_html_d29e072e83962b12.png)

Fig. 13 Sensitivity plot for the MNL model m1

The trade-off table gives a clearer picture of how the choice shares would get affected, when attributes are varied from the baseline design. For attributes "Price" & "Type.of.Wine" the base design offers the highest market share. For the rest of the attributes changing attribute levels to other alternatives increases the share positively. For example, in case of "Aging.time.of.Wine" changing from base design i.e. 4 years to 3 years shows 2.5% increase in market share.

| level share increase
 \<chr\> \<dbl\> \<dbl\>
 Price1 Value(3€-10€) 0.02097490 -0.066935605
 Price2 Popular(10€-15€) 0.087910500.000000000
 Price3 Premium(15€-30€) 0.05684019 -0.031070312
 Price4 Luxury(50€-100€) 0.08170214 -0.006208358
 Brand1 Cantina Toblino 0.06337662 -0.024533879
 Brand2 Cavit 0.087910500.000000000
 Brand3 Ferrari 0.139702980.051792480
 Brand4 Mezzacorona 0.116168310.028257810
 Type.of.Wine1 Red wine 0.07057659 -0.017333907
 Type.of.Wine2 Rose wine 0.06532078 -0.022589726
 Type.of.Wine3 Sparkling wine 0.08626338 -0.001647117
 Type.of.Wine4 White wine 0.087910500.000000000
 Percentage.of.Alcohol1 5.5 % 0.087910500.000000000
 Percentage.of.Alcohol2 7 % 0.107614450.019703951
 Percentage.of.Alcohol3 12 % 0.124436530.036526033
 Percentage.of.Alcohol4 18 % 0.116273680.028363182
 Aging.time.of.Wine1 1 year 0.108143700.020233202
 Aging.time.of.Wine2 2 years 0.07260251 -0.015307992
 Aging.time.of.Wine3 3 years 0.112950710.025040205
 Aging.time.of.Wine4 4 years 0.087910500.000000000
 Aging.time.of.Wine5 5 years 0.105763480.017852976 |
| --- |

####


1.
#### **Choice model considering Customer Heterogeneity**

##### **6.1 Mixed Multinomial logit model**

Mixed Multinomial logit models allow to estimate individual-level coefficients for each respondent, which leads to possibilities to better fit data and produce more accurate predictions than sample-level models, since different persons have varied preferences. The statistical term for coefficients that vary across respondents is random coefficients, hence, the utility function is equal to:

In choice modeling, Correlated Random Parameters means that the parameters (part worths) that represent the preferences of individuals for different attributes (e.g. price, brand, etc) are not independent and have some correlation between them. On the other hand, Independent Random Parameters means that the parameters are completely uncorrelated and have no relationship between them.

The difference between the two methods is in the estimation of the parameters and the assumptions made about the underlying structure of the preferences. In the Correlated Random Parameters approach, the parameters are estimated in such a way that the correlation between them is taken into account. This leads to more accurate and robust results, as it accounts for the fact that individual preferences for different attributes are often not completely independent. In the Independent Random Parameters approach, the parameters are estimated without taking into account the correlations, leading to less accurate results and a higher risk of overfitting. For our project we have tried implementing both the options, first with independent parameters and later with correlation taken into account.

##### **6.2 Mixed Model with Independent parameters**

We can either allow the random parameters to be correlated or independent. If correlation = true, the correlation between the random parameters is taken into consideration by estimating the components of the Cholesky decomposition of the covariance matrix. All of the coefficients in our first model have a normal distribution across the population, and they make up the following vector m1.rpar.

| m1.rpar \<- rep("n", length=length(m1$coef))
 names(m1.rpar) \<- names(m1$coef) |
| --- |

To estimate a multinomial logit model with random coefficients using mlogit, we build a vector specifying which coefficients vary across customers. For the first run, we assume that random parameters are not correlated, therefore we used correlation = FALSE.

| m1.hier \<- mlogit(Choice ~ 0 + Price + Brand + Type.of.Wine +Percentage.of.Alcohol +Aging.time.of.Wine, data = cbc.mlogit, panel=TRUE, rpar = m1.rpar, correlation = FALSE) |
| --- |

As a result, we derived the following coefficients, which illustrate the respondents' average part worth coefficients and how those parameters vary across the respondents:

| Coefficients :
 Estimate Std. Error z-value Pr(\>|z|)
 PricePopular(10€-15€) 2.0662060.5078134.06884.725e-05 \*\*\*
 PricePremium(15€-30€) 1.3833310.4740982.91780.0035250 \*\*
 PriceValue(3€-10€) 1.5987660.5333552.99760.0027215 \*\*
 BrandCavit 0.5650280.4231471.33530.1817780
 BrandFerrari 1.4227950.4355063.26700.0010870 \*\*
 BrandMezzacorona 0.9253980.4295232.15450.0312026 \*
 Type.of.WineRose wine 0.0274850.4347400.06320.9495898
 Type.of.WineSparkling wine 0.2944340.4118430.71490.4746597
 Type.of.WineWhite wine 0.3899640.3505981.11230.2660169
 Percentage.of.Alcohol18 % 0.1741920.4425550.39360.6938722
 Percentage.of.Alcohol5.5 % 0.4024350.3878241.03770.2994221
 Percentage.of.Alcohol7 % 0.2809640.4305370.65260.5140202
 Aging.time.of.Wine2 years -0.2580310.482987 -0.53420.5931762
 Aging.time.of.Wine3 years 0.1087040.3973340.27360.7844053
 Aging.time.of.Wine4 years -0.3700080.405894 -0.91160.3619864
 Aging.time.of.Wine5 years -0.2089510.449284 -0.46510.6418770

 sd.PricePopular(10€-15€) 1.8220120.4362814.17622.964e-05 \*\*\*
 sd.PricePremium(15€-30€) 1.2867400.3254703.95357.702e-05 \*\*\*
 sd.PriceValue(3€-10€) 1.6254420.5621052.89170.0038315 \*\*
 sd.BrandCavit -0.2747310.412973 -0.66530.5058903
 sd.BrandFerrari 1.1753620.4661892.52120.0116950 \*
 sd.BrandMezzacorona 0.7608930.5453871.39510.1629726
 sd.Type.of.WineRose wine 0.5687870.5484331.03710.2996837
 sd.Type.of.WineSparkling wine 1.4971870.5049482.96500.0030265 \*\*
 sd.Type.of.WineWhite wine -0.0233210.316193 -0.07380.9412041
 sd.Percentage.of.Alcohol18 % 1.4751990.3833123.84860.0001188 \*\*\*
 sd.Percentage.of.Alcohol5.5 % 1.8386910.5254303.49940.0004663 \*\*\*
 sd.Percentage.of.Alcohol7 % 1.3542520.5684862.38220.0172092 \*
 sd.Aging.time.of.Wine2 years 0.5044450.3695341.36510.1722261
 sd.Aging.time.of.Wine3 years -0.3769990.368555 -1.02290.3063508
 sd.Aging.time.of.Wine4 years 0.2694750.4640190.58070.5614152
 sd.Aging.time.of.Wine5 years -0.2571630.421165 -0.61060.5414659
 ---
 Signif. codes: 0'\*\*\*'0.001'\*\*'0.01'\*'0.05'.'0.1' '1
 Log-Likelihood: -233.3

 random coefficients
 Min. 1st Qu. Median Mean 3rd Qu.
 PricePopular(10€-15€) -Inf0.83727832.066206452.066206453.29513459
 PricePremium(15€-30€) -Inf0.51543781.383330621.383330622.25122347
 PriceValue(3€-10€) -Inf0.50242171.598765951.598765952.69511017
 BrandCavit -Inf0.37972530.565028300.565028300.75033129
 BrandFerrari -Inf0.63002551.422794961.422794962.21556443
 BrandMezzacorona -Inf0.41218330.925398040.925398041.43861281
 Type.of.WineRose wine -Inf -0.35615590.027485080.027485080.41112605
 Type.of.WineSparkling wine -Inf -0.71540310.294434040.294434041.30427122
 Type.of.WineWhite wine -Inf0.37423410.389964120.389964120.40569412
 Percentage.of.Alcohol18 % -Inf -0.82081420.174192300.174192301.16919877
 Percentage.of.Alcohol5.5 % -Inf -0.83774360.402434900.402434901.64261338
 Percentage.of.Alcohol7 % -Inf -0.63246460.280964360.280964361.19439330
 Aging.time.of.Wine2 years -Inf -0.5982737 -0.25803055 -0.258030550.08221259
 Aging.time.of.Wine3 years -Inf -0.14557780.108703800.108703800.36298543
Aging.time.of.Wine4 years -Inf -0.5517659 -0.37000777 -0.37000777 -0.18824966
 Aging.time.of.Wine5 years -Inf -0.3824045 -0.20895105 -0.20895105 -0.03549757 |
| --- |

Comparing the coefficients and the standard deviation coefficients, we can estimate the heterogeneity between them. Thus, for price attributes, there is no significant difference in the values. Likewise, for Cavit brand the estimate of sd.BrandCavit is about 0.274 lower than the mean estimate of 0.565, which suggests that in general people prefer Cavit over Cantina Toblino. We can also analyze the range of respondent-level coefficients in the random coefficients section. For brandCavit the first quartile is 0.379 (showing a preference for Cavit over Cantina Toblino), the third quartile is 0.750 and the mean is 0.565 (again indicating a preference for Cavit over Cantina Toblino).

Considering the distribution of respondent-level coefficients for rose wine, the majority of respondents slightly prefer rose wine to red wine, as the mean value is equal to 0.027 . Similarly, a number of people tend to prefer red wine over sparkling wine (the first quartile is equal to -0.715), while the majority prefer sparkling wine (the mean is about 0. 294).

Unlike, for 2 years of aging time attribute, the mean estimate is around -0.258, showing the preference of 1 year of aging time over 2 years, whereas the sd. Aging.time.of.Wine2 years is around 0.504, indicating a preference for 2 years of aging over 1 year. Moreover, the negative mean values and the random coefficients for Aging.time.of.Wine 5 years show that there is no fraction of people who prefer 5 years of aging over 1 year. Later, this assumption will allow us to find a strong correlation between the aging time and the brand attributes in order to build the mixed MNL model with correlated parameters. ![](RackMultipart20230204-1-4ijigk_html_621dcde543d491e0.png) ![](RackMultipart20230204-1-4ijigk_html_479515853ff1d5c8.png)

##### **6.2 Mixed model with correlated parameters**

In this model by allowing the parameters to be correlated, the mixed multinomial logit model can account for more complex relationships between the predictors and the outcome variable and can provide more accurate predictions of the probabilities of each category for each individual.

This type of model is useful in a variety of applications, including market research, social sciences, and health sciences, where the outcome of interest has multiple categories and the relationship between the predictors and the outcome is complex and may vary across individuals and categories. Including correlations in the random coefficients, it allows us to estimate based on the data if people who like one attribute also like another attribute.

When we execute the same mixed multinomial model as before, with correlation set to TRUE, we encounter a problem. The outcome says, system is computationally singular. Which means our design matrix is not invertible and therefore can't be used to develop a regression model. This results from linearly dependent columns, i.e. strongly correlated variables. We examined the pairwise covariance (or correlation) of our variables to investigate if there are any variables that can potentially be removed. In order to check this we ran chi-square tests between variables. We found that a lower p-value indicates stronger evidence against the null hypothesis and therefore stronger evidence of dependence between the two variables. Based on this, we could say that the two variables "Brand" and "Aging time of Wine" are more dependent, with a p-value of 0.02779, compared to "Brand" and "Percentage of Alcohol" which has a p-value of 0.04461. So we decided to drop the feature, "Aging time of Wine" and run the mlogit model.

Our model with correlation set to TRUE gives a log-likelihood score as output. The log-likelihood is a measure of how well the specified model fits the observed data. A higher log-likelihood value indicates a better fit, and it is often used as an optimization criterion in statistical modeling. In our case, the log-likelihood value is -233.3 which is the same as the previous case when correlation was set to FALSE. It means that both the models fit the observed data reasonably well. However, the Correlated Random Parameters approach is more practical as it has no underlying assumptions of independence.

##### **6.4 Preference Share Simulator**

The preference share table summarizes the results of the Conjoint Analysis and provides insights into the factors that drive customer preferences and choice behavior. It helps to identify the most preferred and least preferred attribute levels, which can be used to inform product design and positioning decisions. As we build the preference share simulator again for this model, we get results as follows.

| colMeans(shares) Price Brand Type.of.Wine Percentage.of.Alcohol Aging.time.of.Wine
 822 0.22511020 Popular(10€-15€) Cavit White wine 5.5 % 4 years
 610 0.02773092 Popular(10€-15€) Cantina Toblino Sparkling wine 7 % 3 years
**674 0.22545170 Popular(10€-15€) Cantina Toblino Sparkling wine 12 % 3 years**
 738 0.15106438 Popular(10€-15€) Cantina Toblino Sparkling wine 18 % 3 years
 362 0.10127301 Popular(10€-15€) Ferrari Sparkling wine 7 % 2 years
 618 0.10127301 Popular(10€-15€) Ferrari Sparkling wine 7 % 3 years
 638 0.16809678 Popular(10€-15€) Mezzacorona White wine 7 % 3 years |
| --- |

Cantina Toblino Sparkling wine with 12% alcohol content has the highest preference share of 22.54%, followed by Cavit white wine with 5.5% of alcohol and 4 years of aging time. Since the model controlling for heterogeneity usually predicts a bit larger preference share to niche products, we can assume that there is a non-negligible fraction of consumers who would more prefer the products profiles listed above.

![](RackMultipart20230204-1-4ijigk_html_26cf6f90ec74705b.png)

Fig. 14 Correlation plot of the parameters

##### **6.5 Trade off table & Sensitivity Plot**

The trade-off table shows the part-worth or utility value of each attribute level, while the sensitivity plot shows how these values change as one attribute level is changed while keeping all others constant. For baseline and competitor design we reuse the same choices we made previously. The tradeoff table we got is as follows.

| level share increase
 \<chr\> \<dbl\> \<dbl\>
 Price1 Value(3€-10€) 0.1409499 -0.06179818
 Price2 Popular(10€-15€) 0.2313434 0.02859531
 Price3 Premium(15€-30€) 0.1851513 -0.01759674
 Price4 Luxury(50€-100€) 0.1919294 -0.01081869
 Brand1 Cantina Toblino 0.2166581 0.01391005
 Brand2 Cavit 0.2422183 0.03947019
 Brand3 Ferrari 0.1880909 -0.01465716
 Brand4 Mezzacorona 0.2331560 0.03040796
 Type.of.Wine1 Red wine 0.1763217 -0.02642635
 Type.of.Wine2 Rose wine 0.1805134 -0.02223466
 Type.of.Wine3 Sparkling wine 0.1429285 -0.05981955
 Type.of.Wine4 White wine 0.2256721 0.02292402
 Percentage.of.Alcohol1 5.5 % 0.2146006 0.01185251
 Percentage.of.Alcohol2 7 % 0.1503057 -0.05244239
 Percentage.of.Alcohol3 12 % 0.2670324 0.06428435
 Percentage.of.Alcohol4 18 % 0.1507745 -0.05197357
 Aging.time.of.Wine1 1 year 0.2105376 0.00778950
 Aging.time.of.Wine2 2 years 0.2241645 0.02141639
 Aging.time.of.Wine3 3 years 0.2156525 0.01290442
 Aging.time.of.Wine4 4 years 0.2213280 0.01857996
 Aging.time.of.Wine5 5 years 0.2148196 0.01207149 |
| --- |

The sensitivity plot looks as below.

![](RackMultipart20230204-1-4ijigk_html_465195cf9c76e781.png)

Fig. 15 Sensitivity plot for the mixed MNL with correlated parameters

From the trade-off table and the subsequent sensitivity plot, we observe that the base design constitutes dominant market share for attributes such as "Price", "Brand" & "Type.of.Wine". However, much like our previous analysis for the attribute, "Percentage.of.Alcohol", the preference share increases 6.4% if the value is changed from 5.5% to 12%.

1.
#### **Future works:**

While we have taken consumer heterogeneity into account while making predictions in our analysis, we have not yet taken our uncertainty in the parameter estimations into account. This makes it challenging to ascertain what would result in a (statistically significant) share difference between the two alternatives. Although it is feasible to estimate the prediction intervals for these models in a frequentist framework, a Bayesian framework makes this task simpler. So as an enhancement to the current work, we could implement Hierarchical Bayesian Choice Model.

Even if we considered brand of wine as an attribute in our survey, due to practical limitations we had to limit our questionnaire to choice based design only. User's preference may vary purely based on how they associate a brand with a certain type of perception. If we collected responses regarding the perceptual adjectives people associate every brand of wine with, that could help us come up with positioning maps / perceptual maps. They allow us to address relevant questions such as, what constitutes the class or category of a brand or what are the characteristics of consumers' perception etc.

In real life scenarios, a survey is generally conducted with way more respondents than what we could consider in our survey which in our case resulted in large errors. As an improvement to our current work we could broaden our scope of survey in order to accommodate a larger respondent pool. In that case the respondent sample could be representative of the actual consumer population.

1.
#### **Conclusion:**

This work examined the application of conjoint analysis within the customer value concept using the wine market among Italian residents. The results of the tests which identified Price, Type of Wine and Percentage of Alcohol as determinant features have revealed that conjoint analysis is a powerful tool for identifying the importance of different product attributes in creating value for customers. Using this information, it is possible to develop optimal wine configurations for consumers. Models based on the results of conjoint analysis have predictable capacity to spot the response of the market to changes in existing product configurations or price before the actual production decision is made.

1. **Appendix:**

Link to the final code should be pasted here.

1.
#### **References**

[1] Barr, Dale J. "Learning Statistical Models through Simulation in R." _Chapter 5 Introducing Linear Mixed-Effects Models_, https://psyteachr.github.io/stat-models-v1/introducing-linear-mixed-effects-models.html.

[2] Chapman, Chris, and Elea McDonnell Feit. _R For Marketing Research and Analytics_. Springer International Publishing, 2019.

[3] Clark, Michael. "Mixed Models with R." _Mixed Models_, https://m-clark.github.io/mixed-models-with-R/random\_intercepts.html.

[4] Orme, Bryan K. _Getting Started with Conjoint Analysis: Strategies for Product Design and Pricing Research_. Research Publishers LLC, 2020.

[5] Schwarz, Jason S., et al. _Python for Marketing Research and Analytics_. Springer Nature, 2021.

[6] Walton, Noah, and Haitao Du. "How Do I Avoid Computationally Singular Matrices in R?" _Cross Validated_, 1 Jan. 1964, https://stats.stackexchange.com/questions/250350/how-do-i-avoid-computationally-singular-matrices-in-r.

