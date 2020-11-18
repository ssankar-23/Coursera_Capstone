---


---

<h1 id="battle-of-the-neighborhoodsbr-comparison-of-communities-in-trinidad-and-tobago">Battle of the Neighborhoods:<br> Comparison of Communities in Trinidad and Tobago</h1>
<h3 id="description-of-the-problem">Description of the Problem</h3>
<p>Trinidad and Tobago, though small in area, is a developing nation, and is eager to invest in companies or businesses that are willing to be opened no matter the type, in an effort to stimulate and diversify the economy. In light of the current economic crisis associated with the fallout from COVID-19, businesses must be smart in choosing their locations, in order to get a good start at success. The aim of this project will be to determine where would be the best place to open a business in Trinidad and Tobago by comparing the top ten (10) venues for each community as well as population and crime data.</p>
<h3 id="introduction">Introduction</h3>
<p>The twin island nation of Trinidad and Tobago is located within the Caribbean, West Indies. It is a developing nation with the third highest GDP per capita based on purchasing power parity (PPP) in the Americas after the United States and Canada (<em>World Economic Outlook Database, October 2017</em>). The country has a population of approximately 1,363,985 people, covering an estimated 5100 km<sup>2</sup> which leads to a population density of 273 per km<sup>2</sup>. This value, however, varies greatly for each community or city.</p>
<p><img src="https://www.freeworldmaps.net/centralamerica/trinidad/trinidadtobago-map.jpg" alt="Map of Trinidad and Tobago)"><br>
Fig. 1 Map of Trinidad and Tobago, (<em>Source: <a href="http://freeworldmaps.net">freeworldmaps.net</a></em>)</p>
<p>The majority of the population within Trinidad (the larger of the two), lies within the more urban areas located in the western part of the country. These also correspond to a higher number of businesses in these areas. Even though Trinidad and Tobago has the potential to be a booming country for the business community, Trinidad and Tobago, however, has over the last few decades, a very high crime rate with murder rates near to or crossing 500 each year for the past decade. This has the potential to ruin a business, especially one that is newly established. As such, many investors have been turned off from the idea of starting a business. Therefore, it is imperative this must be factored in when determining the location of a business.</p>
<h3 id="data">Data</h3>
<p>As Trinidad and Tobago is such a small country, updated information is very difficult to find, with not much being made available for use. The data for this project will consist of:</p>
<ul>
<li><strong>Community / Municipality Data</strong> - Names of communities and population data scraped from the City Population site (<a href="https://www.citypopulation.de/en/trinidad/admin/">https://www.citypopulation.de/en/trinidad/admin/</a>) and cross referenced with data from the Central Statistics Office of Trinidad and Tobago.</li>
<li><strong>Geocoder Location Data</strong> - From <code>geopy</code> used to retrieve the location data for each community.</li>
<li><strong>Foursquare API Information</strong> - To explore the venues available for each community in Trinidad and Tobago and collect their location information.</li>
<li><strong>Crime Statistics</strong> - Total reported serious crimes for 2018 sourced from the Central Statistics Office of Trinidad and Tobago (<a href="https://cso.gov.tt/wp-content/uploads/2020/01/Total-Number-of-Serious-Crimes-by-Police-Division-Station-2018.xls.xls">https://cso.gov.tt/wp-content/uploads/2020/01/Total-Number-of-Serious-Crimes-by-Police-Division-Station-2018.xls.xls</a>). The list of serious crimes in this list consists of murder, shootings, sexual offences, kidnapping, burglaries, robberies, fraud, larceny, narcotics, possession of firearms, etc.</li>
<li><strong>.GEOJSON Data</strong> - The .geojson file used in this project was created by myself as none was available.</li>
</ul>
<h3 id="methodology">Methodology</h3>
<p>Firstly, all the required libraries and packages were imported. Then the following steps were taken:</p>
<ol>
<li>The data for this project was sourced from the site, City Population ( <a href="https://www.citypopulation.de/en/trinidad/admin/">https://www.citypopulation.de/en/trinidad/admin/</a>), which has up to date information on the population of cities around the world. These numbers were cross referenced with the 2011 census data from the Central Statistical Office of Trinidad and Tobago (<a href="https://cso.gov.tt/subjects/population-and-vital-statistics/population/">https://cso.gov.tt/subjects/population-and-vital-statistics/population/</a>). This was placed in a dataframe for easy handling and analysis.</li>
</ol>
<p align="center">
  <img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/orignal_web_scrape-df.jpg">
</p>    
<ol start="2">
<li>An address column was added to the dataframe which consisted of the name of the community and Trinidad and Tobago such that the address can be fed through <code>geocoder</code> and used to obtain location data.</li>
</ol>
<p align="center">
  <img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/new_address_column.jpg">
</p> 
<ol start="3">
<li>This method was used as the other shown in the <code>geocoder.google</code> function produced no results and caused the allotted free searches to be used up. The dataframe was filtered and cleaned so that only the data to be used in the project would be present. The new dataframe obtained is as shown below. The communities with no location data were removed from the dataframe and not processed. The number of rows went from 608 to 479.</li>
</ol>
<p align="center">
  <img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/df_locations.JPG">
</p> 
<ol start="5">
<li>
<p>To display the locations of these communities on a map, the <code>geocoder</code> package was used to obtain the latitudinal and longitudinal points for Trinidad and Tobago so that it can be used as the starting point for the map. Then <code>folium</code> was used to plot these points.<br>
<img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/venues_tt.png" alt=""></p>
</li>
<li>
<p>In order to obtain the venues data from Foursquare, it needed to be initialized with the client ID, secret and version.</p>
</li>
<li>
<p>Next the communities were explored using Foursquare and the function <code>getNearbyVenues</code> from the tutorial. The limit for the number of venues was set at 100 and the radius as 500 metres. A GET request URL was then created. A GET request was sent and the results were examined. This was repeated for all the communities in Trinidad and Tobago.</p>
</li>
<li>
<p>The results from Step 6 were stored in a new dataframe <em>tt_venues</em>.</p>
</li>
<li>
<p>To analyze each community, dummy variables for each venue category were created to convert categorical data into binary.  The mean of the frequency of venues of each category in the respective community was found.</p>
</li>
<li>
<p>The top 10 most common venues for each community was found and stored in a new dataframe.</p>
</li>
</ol>
<p align="center">
  <img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/most_comm_venues.png">
</p>
<ol start="10">
<li>
<p>The <em>k-means</em> machine learning was used to cluster the data based on their venue similarities. <em>K-means</em> is unsupervised, fast and easy to interpret. It works with unlabeled data and since many of the venues in this study were reoccurring, this method of machine learning was a good match.</p>
</li>
<li>
<p>The number of clusters chosen were five (5) and the algorithm ran through the data resulting in each community being grouped in one of the five clusters.</p>
</li>
<li>
<p>This was then displayed on a map of Trinidad and Tobago.</p>
</li>
<li>
<p>Next, population (2011)  and crime data (2018)  obtained from the Central Statistical Office of Trinidad and Tobago were used to create a new dataframe. This was grouped by the main municipalities in Trinidad for easier analysis. For this comparison, only Trinidad (the bigger of the two islands) would be focused on. This data would be used to compare the cluster data to the population and crime data in order to determine the best locations for a business.</p>
</li>
</ol>
<p align="center">
  <img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/table.png">
</p>
<ol start="14">
<li>
<p>Data and other resources are difficult to find for Trinidad, therefore a .geojson file for each municipality was created by myself to be used in the choropleth maps.</p>
</li>
<li>
<p>Using <code>folium</code> choropleth maps were generated for the population distribution as well as the crime distribution in Trinidad.</p>
</li>
<li>
<p>The cluster points previously generated were then overlayed on these maps to determine any patterns or correlation between them.</p>
</li>
</ol>
<h3 id="results">Results</h3>
<p>From the <em>k-means</em> algorithm, using <em>k</em> = 5, the following map was generated:</p>
<pre><code>Red = Cluster 0, Purple = Cluster 1, Blue = Cluster 2, Green = Cluster 3, Orange = Cluster 4
</code></pre>
<p align="center">
	<img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/clusters_tt.png">
</p>
<p>Next, using the population data, a choropleth was created for Trinidad:</p>
<p align="center">
	<img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/pop.png">
</p>
<p>The clusters created were then overlayed on the population choropleth:</p>
<p align="center">
	<img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/pop_venues.png">
</p>
<p>The same was repeated using the crime data:</p>
<p align="center">
	<img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/crime.png">
	<img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/crime_venues.png">
</p>
<p>For the 5 clusters obtained, each were categorized by the following venues:</p>
<ul>
<li><strong>Cluster 0</strong> (Red) - Bar, Women’s Store, Restaurants (Fish &amp; Chips, Eastern European, Chinese), Field, Farmer’s Market, Farm</li>
<li><strong>Cluster 1</strong> (Purple) - Restaurants (Fast Food, Chinese, Diner, Fish &amp; Chips), Hotels, Women’s Store, Field, Grocery Store, Farm, Farmer’s Market</li>
<li><strong>Cluster 2</strong> (Blue) - Chinese Restaurant, Women’s Store, Eastern European Restaurant, Fish &amp; Chips, Field, Farm</li>
<li><strong>Cluster 3</strong> (Green) - Bar, Women’s Store, Electronics Store, Fish Market, Fish &amp; Chips, Field, Farm</li>
<li><strong>Cluster 4</strong> (Orange) - Beach, Pool, Women’s Store, Electronics Store, Market, Fish &amp; Chips, Field, Farm</li>
</ul>
<p>From this, we can assign names that describe each cluster:</p>

<table>
<thead>
<tr>
<th>Cluster Label</th>
<th>Assigned Name</th>
</tr>
</thead>
<tbody>
<tr>
<td>Cluster 0</td>
<td>Recreation</td>
</tr>
<tr>
<td>Cluster 1</td>
<td>Social</td>
</tr>
<tr>
<td>Cluster 2</td>
<td>City Essentials</td>
</tr>
<tr>
<td>Cluster 3</td>
<td>Life</td>
</tr>
<tr>
<td>Cluster 4</td>
<td>Outdoor</td>
</tr>
</tbody>
</table><h3 id="discussion">Discussion</h3>
<p>Trinidad is a small country in the Caribbean that is well known for its party culture. Places to eat and “hang out” dominate all of the clusters generated. As previously mentioned in the introduction, most of the developed and populated areas are located in the western parts of Trinidad, with much of the eastern regions being scarcely dotted with venues. From the clusters generated, it is visible that the majority of communities are grouped in either Cluster 0 or Cluster 1.</p>
<p>Cluster 0 points are located close by but are slightly more spread out from the communities centre. These points represent businesses or venues that are more laid back and are meant for recreational activities. Bars can be seen to dominate this cluster in addition to restaurants that are traditionally “take-out”. Fields for exercise as well as farms and farmer’s markets are a common occurrence in this cluster. Businesses that <strong>target the older population and mature crowd for a more relaxed environment</strong>, should consider areas in Cluster 0.</p>
<p>Upon further analysis, we can see that Cluster 1 points are distributed mainly at town or community centres which are most likely to encounter the highest foot traffic where persons tend to gather in higher numbers to socialize. These include food places to dine in, to a variety of shops, clubs and malls. For <strong>businesses that require high traffic areas, buzzing with activity, catering for the younger crowd</strong>, Cluster 1 points would be best suited.</p>
<p>In Cluster 2, the top 10 most common venues were grouped perfectly with no variance in any of the points. These are located in or close to boroughs and cities in Trinidad and consist of the following category groups: Chinese Restaurant; Women’s Store; Eastern European Restaurant; Fish &amp; Chips Shop; Field; Fast Food Restaurant; Farmers Market; Farm; Falafel Restaurant; Event Service. As this cluster is specific to its target group (cities and boroughs) the two remaining locations to have businesses in this cluster would be within <strong>Arima</strong> and <strong>Chaguanas</strong>.</p>
<p>Cluster 3 points is again topped by Bars being the most common venue. These points are similar to those in Cluster 1 in which they are located off of the main community centre. There is barely any variance in the venue types for the top 10 most common venues. This cluster was labeled as ‘Life’ as it constitutes venues which are generally a part of everyday life in Trinidad. <strong>Venues to drink, shop, exercise and gather fresh produce without having to be in the busy town centres are aimed more towards the older crowd (&gt;45 years)</strong>.</p>
<p>The venues in Cluster 4 are almost all exclusively outdoor activities within the more rural areas. These are targeted around the coast of Trinidad where beaches and other scenic attractions may be present. Fields, farms and markets are also prevalent in these areas due to the large expanse of land available for farming and other outdoor recreational activities. Venues in this cluster are for the more outgoing persons and can be seen to be distributed more in the western and northern areas. <strong>The eastern coast possesses potential for development in such an area</strong>.</p>

