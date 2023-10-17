### Problem Statement
The main passenger transport in Singapore comprises of the public bus, train system and taxis. A major form of transportation is rail: The Mass Rapid Transit (MRT) which now has more than 140 stations across six lines, and the Light Rail Transit (LRT) with 41 stations across three lines. The bus system is currently operated by four companies offering different types of transport services such as midnight bus service and feeder bus services that connects passengers within an estate. Currently, there are six taxi operators, and the taxis can be flagged along the street, at designated taxi stands or booked online.

Average number of passengers per day using public transport in Singapore is 6.39 millions passengers which are almost 100% of population.

Weather especially rain is considerted to have great impact on the usage on public transportation.

The objective of this report is to help audiences who operate the public transportation to be able forecast the demand on public transportation better, given by the number of rainy days and the rain volume, hence being able handling its capacity better, or even adjust for better services

Therefore we will address the following problems.
 - what are the breakdown% of public transport usage across mode of transportation in Singapore?
 - What are the trends of public transport usage across mode of transportation? and What are the trends of rainy days and rain volumme across the years?
 - Does the rainy days and rain volumes have impact on demand for public transport across mode of trasnportation?
 - What are recommendation possible from the finding above?


### Conclusion & Recommendation
 
 
 - what are the breakdown% of public transport usage across mode of transportation in Singapore?
 
 48% of passenger ridership are buses
 38% of passenger ridership are MRT
 12% of passenger ridership are buses
 2% of passenger ridership are buses
     
![ridershipbreakdown_bymodetransport](/image/ridershipbreakdown_bymodetransport.png)


 - What are the trends of public transport usage across mode of transportation? and What are the trends of rainy days and rain volumme across the years?

Passenger ridership overall has increase year on year especially for MRT and Bus.while rainy days, average rainvolume per day(mililitre), max rain volume in highest day (mililitre) has flat trend with some flutation over the years.

 ![rainvolumetrend](/image/rainvolumetrend.png)
 ![rainydaystrend](/image/rainydaystrend.png)
 ![transporttrend](/image/transporttrend.png)


 - Does the rainy days and rain volumes have impact on demand for public transport across mode of transportation?

Rainy days and rain volumes has negative impact on demand for public transport across MRT, LRT, bus, and taxi, with heavy impact on MRT, LRT, and bus, and moderate impact on taxi. These difference in impact between mode of transportaion may come from taxi does not required walking distance compared to MRT, LRT, and bus.

![rain&transportcorrelation](/image/rain&transportcorrelation.png)


 - What are recommendation possible from the finding above?

1) operators of MRT, LRT, bus, and taxi should include rain forecast as part of features in transportatin demand prediction.
2) to perform better forecast, daily level data of rain and usage of public transportation are required. 
3) for operators to increase the demand for public transportation, the infrastruce to help prevent the rainfall along the walking distrance to train stations or bus stops are required. we can start this project by looking at the train station and bus stop with high demand during rainy season. or the operators can provide the sales of umbrella or raincoat during rainy season at the bus stops or train station. 

---

### Datasets

we use total 4 data sources. all of them are from https://beta.data.gov.sg/

#provided data 
1 rainyday_mth = pd.read_csv("../data/rainfall-monthly-number-of-rain-days.csv")
2 rainvolume_mth = pd.read_csv("../data/rainfall-monthly-total.csv")
3 rainhighestday_mth = pd.read_csv("../data/RainfallMonthlyHighestDailyTotal.csv")

#additional data
4 trans_ridership_yr = pd.read_csv("../data/PublicTransportUtilisationAveragePublicTransportRidership.csv")

---

### Data Processing

based on our problem statement,
#we are going to check the data and then combine the 4 datasets into 1 datasets with year summary for each row
    # rainyday_mth
    # rainvolume_mth
    # rainhighestday_mth
    # trans_ridership_yr

There are 5 steps in this data processing

step 1) check data set

step 2) transform these following 3 datasets from month summary datasets into year summary datasets
    # rainyday_mth --> rainyday_year
    # rainvolume_mth --> rainvolume_yr
    # rainhighestday_mth --> rainvolume_yr
    
step 3) combine these 3 datasets above into one dataset with year as key 
    # rain_yr_join
    
step 4) transform "trans_ridership_yr" data set by pivoting values into attributes and summarizing into year summary per row
    # trans_ridership_yr --> trans_ridership_yr_join

step 5) combine "rain_yr_join" data set with "trans_ridership_yr_join" dataset, and then filter year before 2000 to handle missing values
    # rain_vs_publictransport
    # rain_vs_publictransport_start2001
