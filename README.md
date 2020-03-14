# Apartments-Listings-NYC-Analysis-and-Modeling

**IN PROGRESS!** 

<img src="images/apartment-search.png" width=100%>


# Find somewhere to lay your head in the city that never sleeps. Make better decision for affordable apartment hunt in NYC with data. 

## Introduction

For international students it is hard to manage their finances is USA. Especially, when your parents are not super rich and your are not allowed to work more then 20 hours a week. 

Affordable and convenient accommodation is a basic requirement to live in States. As my university is in NJ (Drew University, Madison NJ) and I planing to do summer internship in New York City. It would require me to move to NYC, as commuting from NJ would be a time consuming and less effective. Hence, I decided to support my decision for apartment hunt with data analysis and machine learning modeling. 

For understating of NYC neighborhoods: Read [here](https://www.moneyunder30.com/renting-in-nyc).


## Data Source

My first concern was how can I get the data for such analysis?
Well, I decided to scrap web for gathering relevant data. Most websites (like listed below) have strict rules for web scarping. Obviously, because of the reason that they don't want others to take competitive advantage from their data.  
-	streeteasy.com <br>
-	cityrealty.com <br>
-	zillow.com<br>

Many popular websites have their APIs available. <br>
- [zillow.com](zillow.com/howto/api/faq.htm)<br>
It impose some limitations like: access to only historical data and limited number of API calls. <br>
- [realtor.com](https://www.realtor.com/) <br>
Also a good source for the data with different paid plans.

Anyways, if its on the web then its accessible either easily or a hard way. Moreover,I found a real estate website [renthop.com](renthop.com) who's design is simple enough for web scraping.

Do you wonder is scrapping legal to do so? Cases in which its illegal: Read [here](_docs/Is-web-scraping-legal-2.pdf).

#### Website Inference

![renthopes.com](images/renthopes.com.png)

## Data
- Url 
- Address
- Neighborhood 
- Number of Beds
- Number of Baths 
- Rent in dollars

More Data
- Zip codes of areas are acquired using **Google maps API** calls. 

## Initial Data Prepossessing
*Flexes* have large number of missing values. In this case it means the apartment have no flex at all. In addition, we can see a couple of missing addresses. Which could be most probably because of a few scrapping anomalies, Assuming that website would not allow to post a listing without adding the address first. 

<img src="images/data-info1.jpg" width=40%>

After getting related zip codes from Google Maps API. We lost many instances because we are unable to get corresponding zip codes. If we look at the interface of website we can find that the reason behind is that we are not parsing individual listing pages, we are parsing  pages which only consists of listings overview. And when the address is larger in length then it is squeezed down like *2728, upper east side, .... NY*. 

<img src="images/data-info2.jpg" width=40%> 

**Remedy:** Improve data capturing process. 
For now we should proceed, even though it could add some hidden bias in the model. However, we can come up with the base setup, which can be improved in further iterations.
 

## Exploratory Data Analysis 
#### Top 10 places with most listings 
<img src="images/most_listings_top_10.jpg" width=50%>

Hell's kitchen, Midtown Manhattan has listings are in Manhattan

#### Mean rent at the neighborhoods
Bronx and queens have some neibourhoods with cheap retal. However, inquires from a few Newyorkers and seaching online I found these areas have high crime rate. 

Furhtermoere, places like *Theater District, Midtown Manhattan* and *Hudson Square, SoHo, Downtown Manhattan* are very expensive.

<img src="images/mean-rent-at-nhoods.jpg" width=50%>

Some places are super expensive as their Mean rent exceeds $6000

<img src="images/boxenplot_nhood_avg.png" width=50%>

**Neighborhoods with mean rent more then $6000**

<img src="images/nhood_expensive.jpg" width=50%>


#### Rental By Zip Codes
Rent ranges from $785  to $10353. Mostly rent is between $2000 to $4200 range on average. With very few number of listings on extreme.<br>
![Outliers](images/boxenplot_outliers_zip_avg.png)

#### Map (Average rent):

Areas with average above 6000 are excluded (only for maps). As they are outliers and more expensive then usual. They makes map a little difficult to interpret affordable apartments, as the color legend stretches to the limit of these oultilers.

![NYC Map](images/map1.png)

We can observe that Manhattan is Expensive then other boroughs.

#### **Manhattan** (neighborhoods):

![Manhattan Map](images/manhattan_map1.png)

Midtown Manhattan and Upper East Side are expensive as compare to Upper Manhattan.

*Black shaded regions means we either don't plot on that areas or we don't have related data.*


**IN PROGRESS!** 