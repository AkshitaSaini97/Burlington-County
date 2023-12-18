# Understanding Accessibility
## _________________________________________________________________________________________________________________________
## By Akshita Saini (MCRP), Edward J Bloustein School of Planning and Public Policy, Rutgers University 
(This is the final project for the course: Command Line GIS)

### Research Question: Are the essential services and transit area (0.5 mile as walkable distance) distributed equitably? Are they located in areas with population potentially at disadvantage and low-income census tracts?
### Objective: To map the spatial distribution of essential services and transit area in Burlington County and overlay it over median income and indicators of potential disadvantage at census tract level

### Datasets:
1. Median Income| Source: American Community Survey (5-year estimates), 2015-2019
   The dataset is in table form which was merged with the Burlington's spatial data to map them.
2. Indicators of Potential Disadvantage | Source: DVRPC Open Data Center, 2021
   The dataset is downloaded in GeoJSON format, where the subset is created for census tracts of Burlington County. The crs is changed from WGS84 to     NJSP
3. Equity through access (or Essential Services) | DVRPC Data Center
   It is a point spatial dataset used both in shp and GeoJSON format. The crs is changed to compliment static and interactive mapping. The dataset is    clipped to Burlington using Burlington Boundary
4. Transit services
  (Rail Stations of NJ Transit (NJGIN)
  Bus Stops of NJ Transit by Line (NJGIN)
  Light Rail Stations of NJ Transit (NJGIN)
  Path Station Locations (NYC Open Data)
  Passenger Rail Stations (in the DVRPC area, filtered before export to only PATCO stations in NJ, not SEPTA on the PA side or the NJ Transit RIVER     line since we have it above in Light Rail Stations)
  First, all the transit datasets are converted into dataframes and their crs is changed to njsp. Finally they are all merged into one geodataframe     using union (overlay function). To create a transit area of 0.5 mile - buffer function is used around all the transit stops and unary union is used   to dissolve all the buffers into one.

## Spatial distribution of median income and potential disadvantaged population
![map1](https://github.com/AkshitaSaini97/BurlingtonMap/assets/152640805/775fe1ce-b996-4373-82f5-b91122ea60b3)

## Spatial Distribution of Essential Services in relation to median income and potentially disadvantaged population
![map2](https://github.com/AkshitaSaini97/BurlingtonMap/assets/152640805/29fa13b7-c633-41ad-bcdb-ca12bdd57752)

## Spatial Distribution of Transit service area in relation to median income and potentially disadvantaged population
![map3](https://github.com/AkshitaSaini97/BurlingtonMap/assets/152640805/b2468a77-277e-4c51-b885-c106bd66850b)

## Interactive map to view the type of services and coverage of transit service area in Burlington County
<iframe src='interactive_map.html' width = '900' height = '900' ></iframe>
You can also explore [this map as its own web page here](interactive_map.html)
