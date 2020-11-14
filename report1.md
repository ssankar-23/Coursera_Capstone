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
<ol>
<li>
<p>The data for this project was sourced from the site, City Population ( <a href="https://www.citypopulation.de/en/trinidad/admin/">https://www.citypopulation.de/en/trinidad/admin/</a>), which has up to date information on the population of cities around the world. These numbers were cross referenced with the 2011 census data from the Central Statistical Office of Trinidad and Tobago (<a href="https://cso.gov.tt/subjects/population-and-vital-statistics/population/">https://cso.gov.tt/subjects/population-and-vital-statistics/population/</a>). This was placed in a dataframe for easy handling and analysis.</p>
<p><img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/orignal_web_scrape-df.jpg" alt="(1)"></p>
</li>
<li>
<p>An address column was added to the dataframe which consisted of the name of the community and Trinidad and Tobago such that the address can be fed through <code>geocoder</code> and used to obtain location data.</p>
</li>
</ol>
<p><img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/new_address_column.jpg" alt=""></p>
<ol start="3">
<li>This method was used as the other shown in the <code>geocoder.google</code> function produced no results and caused the allotted free searches to be used up. The dataframe was filtered and cleaned so that only the data to be used in the project would be present. The new dataframe obtained is as shown below:<br>
<img src="https://github.com/ssankar-23/coursera_capstone/raw/master/images/df_locations.JPG" alt=""><br>
The communities with no location data were removed from the dataframe and not processed. The number of rows went from 608 to 479.</li>
<li></li>
</ol>

