# AustinCrimeAnalysis

# Content
This Data is taken from Austin Police Department(APD) data of crime reports. The data represents only 
calls for police where a report was written. The dataset depicts only the highest level offense of an 
incident.
# Acknowedgement
City of Austin Open data portal. Crime Reports Data. Retrieved from<br/> https://data.austintexas.gov/Public-Safety/Crime-Reports/fdj4-gpfu
# Inspiration
Based on the time, location, place, etc. of report can the police actually guess the severity
of a crime and with this can they react faster to 911 calls or prevent crimes as such?<br/>
Can we find a pattern of crime happening in a particular region and can this insight help us prevent/reduce 
the probablity of future crimes?
# Size of Data
Rows - 2,116,499<br/>
Columns(Attributes) - 27
# What next?
Performing data analysis steps on this data we try to find and answer a few hypothesis,<br/>
Is there a useful pattern that can be derived from the given data?<br/>
Can a classification model be built to predict the nature of a crime given the time and location of the report?<br/>
Do the actual crimes and the area in which they occur exhibit a trend?<br/>
# Attributes
The raw data taken from google public bigquery dataset has the following attributes:<br/>
1) unique_key - A unique identification number for the record<br/>
2) address - Full address of where the incident occcured<br/>
3) census_tract - Census tract value for the address<br/>
4) clearance_date - Date and time when the case was closed<br/>
5) clearance_status - Status of the case<br/>
6) council_district_code - District code of the place where the incident occured<br/>
7) description - Subcategory of the primary nature of crime<br/>
8) district - Police district code where the incident occured<br/>
9) latitude<br/>
10) longitude<br/>
11) location - (lat, long) value of incicdent address<br/>
12) location_description - description of location where the incident occured<br/>
13) primary_type - type of crime according to the NIBRS/UCR code<br/>
14) timestamp - time when the incident occcured<br/>
15) x_coordinate<br/>
16) y_coordinate<br/>
17) year - year in which incident occured<br/>
18) zipcode - zipcode where the incident occured<br/>

# Datastudio Report
This pie chart shows the case status of cases. <b>Dimension:</b> 'clearence_status' <b>Metric:</b> Count of all the cases where 'case_status' is not null.<br/>
<img src="Screenshot (22).png"></img><br/>
From the pie chart we see that 82.6% of the cases go uncleared. The following Line chart shows The number and type of crimes committed by month for the year 2015.<br/>
<img src="Screenshot (23).png"></img> <br/> One basic observation is that Theft is higher compared to other crimes followed by burglary and assault. As expected we cannot see a linear trend in some crimes(like Murder,etc.) while other crimes(like Theft, etc.) remain almost unchanged.
# Data Ingestion
The raw data is already available on bigquery public dataset on google cloud. we copy the data into our project dataset.
We then run few queries first to take a look at the data and look for any problems in any of the rows. 
Next step is to trim the data to get a specific time period, we only keep records from 2014-01-01 to 2016-12-31. 
The most important categorical value 'primary_type' is redundant, we change this to have 7 primary types of crime [Rape, Theft, Robbery, Assault, Burglary, Murder, Homicide]
For further preprocessing we use notebooks and find that location value is missing for more than half of the entries. By using python's inbuilt geopy package.

# ML
Our plan is to use pyspark to split the data into training and test and then do a logistic regression model and check results.
And then use different models  from which we get the error, rmse, etc. and compare for all models. Then decide on which model would be a better fit our data.

# References
[1] Chen, H; Chung, W; Xu, JJ; Wang, G; Qin, Y; Chau, M. 2004. Crime data mining: A general framework and some examples. Available at:http://hdl.handle.net/10722/45461 <br/>
[2] S. B. Kotsiantis, D. Kanellopoulos and P. E. Pintelas. 2006. Data Preprocessing for Supervised Leaning. Volume 1, Number 1,  INTERNATIONAL JOURNAL OF COMPUTER SCIENCE. <br/>
[3] John M. Chambers, William S. Cleveland, Beat Kleiner, Paul A. Tukey. 2017. Graphical Methods for Data Analysis. Availabble at: https://content.taylorfrancis.com/books/download?dac=C2017-0-66641-7&isbn=9781351080750&format=googlePreviewPdf

