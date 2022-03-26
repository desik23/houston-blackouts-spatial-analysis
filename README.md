**Spatial Analysis Assignment**

2021-10-24

*Desik Somasundaram and Hanna Weyland*

**Introduction**

In this assignment, we looked at data from the severe winter storms that occurred in Texas in February 2021. Specifically, we estimated how many homes in Houston went without power as a result of the storm as well as investigated the differences in recovery of various suburbs in Houston. We also looked at any socioeconomic factors that could potentially be predictors of a community’s recovery from a power outage. 


**Data Collection and Analysis**

Data was obtained from the Visible Infrared Imaging Radiometer Suite (VIIRS) on the the Suomi satellite. Using [NASA's WorldView](https://worldview.earthdata.nasa.gov/?v=-101.58556300546445,26.512049387520236,-90.19768525022724,32.331064328350124&z=2&l=Reference_Labels_15m,Reference_Features_15m,Coastlines_15m,VIIRS_SNPP_DayNightBand_At_Sensor_Radiance,VIIRS_SNPP_CorrectedReflectance_TrueColor(hidden),MODIS_Aqua_CorrectedReflectance_TrueColor(hidden),MODIS_Terra_CorrectedReflectance_TrueColor(hidden)&lg=true&t=2021-02-07-T12%3A00%3A00Z), we examined the days around the storm to determine which datasets to use. Since there were a number of days with cloud cover, 2021-02-07 and 2021-02-16 were found to be the best days to analyze the extent of the power outage as a consequence of the storm. 

We used data distributed through NASA's [Level-1 and Atmosphere Archive & Distribution System Distributed Active Archive Center (LAADS DAAC)](https://ladsweb.modaps.eosdis.nasa.gov/) to download four different datasests needed for this analysis. The VIIRS data is distributed as a 10x10 degree tile in a sinusoidal equal-area projection. Houston lies on the border between tiles and thus four different datasets (two sets of data for each day, one for tile h08v05 and the other for tile h08v06one) were needed to account for Houston being on the border of tiles. Data needed to be combined into a single object for each day of the storm (2021-02-07 and 2021-02-16) resulting in one dataset for each day. Data was read in using a provided code.   


Night lights intensity after the storm was subtracted from the night lights intensity before the storm to get the difference in night lights intensity caused by the storm. Data was reclassified so that any location that experienced a drop of more than 200 $nW cm^{-2} sr^{-1}$ was classified as a blackout.

This data was cropped to our region of interest (ROI) of the metropolitan Houston area using a bounding box and turning coordinates into a polygon.  


**Road Data**

Highways typically produce light pollution due to traveling cars and thus needed to be considered for this analysis in order to minimize interference between headlights and residential lights. A 200m buffer was placed around all highways to minimize falsely identifying areas with reduced traffic as areas without power. Anything producting lights within 200m of a highway was ignored. Highway data from OpenStreetMap (OSM) was used to map out the various roads in Houston. Data was downloaded from [Geofabrik’s download sites ](https://download.geofabrik.de/) and a shapefile was retrieved of all of the highways in Texas.


**Building Data**

Similarly, housing data was obtained using Geofabrik’s Texas subset of OSM buildings but needed to be subsetted to include only buildings that were either residential, apartments, house, static_caravan, detached. 


**Census Data**

Socioeconomic data was obtained from the [U.S. Census Bureau’s American Community Survey ](https://www.census.gov/programs-surveys/acs) for Texas census tracts in 2019. Contents of the data was explored to find different socioeconomic factors that could be a potential predictor of a community’s recovery from a power outage. In an article produced in [the Rockefeller Foundation](https://www.rockefellerfoundation.org/case-study/frozen-out-in-texas-blackouts-and-inequity/), it was found that minority groups were four times more likely to suffer a blackout than predominately white areas. Thus, we chose to analyze populations of people in Houston that identified as either Hispanic or Latino by origin to see if the blackouts corresponded with locations of minority populations. 

**Results**

After combining the ethnicity data from the census tract data with the data of the houses that experienced a blackout, it was found that areas of higher Hispanic or Latino identifying people were potentially more likely to experience a blackout. After analyzing the map consisting of only those who identified as Hispanic or Latino and the map overlaid with the blackout data, it can be seen that areas with a higher population of people who identify as Hispanic or Latino were more likely to experience a blackout. Typically areas with 3,500-10,500 people who identify as Hispanic or Latino were typically in blackout zones. Although other minority groups were not taken into account, it can be concluded that minority populations, specifically looking at Hispanic or Latino identifying populations were more susceptible to power outages. However, a more rigorious analysis would need to be conducted in order to confirm these findings. 

