# GIS Portfolio
Welcome to my GIS portfolio. Below you can browse a selection of maps and applications I created for professional development, educational and private purposes.

## Projects List
[Measuring Connectivity of Urban Green Spaces for Countering Fragmentation](https://github.com/xJKLx/GIS?tab=readme-ov-file#ecosystem-management-measuring-connectivity-of-urban-green-spaces-for-countering-fragmentation)  <br>
[Modelling Spatial Dependency of Dengue Transmission in Singapore](https://github.com/xJKLx/GIS?tab=readme-ov-file#modelling-spatial-dependency-of-dengue-transmission-in-singapore)    <br>
[GIS Analysis in Building Resilient Settlements](https://github.com/xJKLx/GIS?tab=readme-ov-file#gis-analysis-in-building-resilient-settlements)    <br>
[Cartography - Wilsons Promontory National Park](https://github.com/xJKLx/GIS?tab=readme-ov-file#cartography)    <br>
[Spatial Patterns of Agglomeration in one-north](https://github.com/xJKLx/GIS?tab=readme-ov-file#spatial-patterns-of-agglomeration-in-one-north)    <br>

# Ecosystem Management: Measuring Connectivity of Urban Green Spaces for Countering Fragmentation 

*Overview*  <br>
In this research project, the Bukit Batok Nature Corridor (BBNC) established as part of an island-wide network of park connectors in Singapore to enhance ecological connectivity between natural areas in urban landscapes was used as a case study of the effectiveness of such greenways, as a countermeasure to fragmentation of natural habitats in urban areas.  

## Obtaining spatial datasets and working with remote sensing data
The phased implementation of the BBNC (blue polygon) and its effect on connectivity was measured in a study area encompassing the BBNC and surrounding areas within a 5km radius (red rectangle). BBNC serves as an intermediate node between existing natural areas allowing the movement of wildlife between core biodiversity areas - Central Catchment Nature Reserve and Western Water Catchment. Satellite imagery sourced from ESRI and land use layers from Urban Redevelopment Authority (URA) Master Plan 2019.  

![BBNCarea](https://github.com/xJKLx/GIS/assets/157556286/86c6c90d-87f7-4691-a60b-74a280f49eb2)

Road network in the study area (A) represents the fragmentation geometry inhibiting movement of wildlife between natural habitats. The reduction effect of the BBNC (blue polygon) on the fragmentation geometry is shown (B) by removing road features intersecting with BBNC connectors polygons in QGIS using expression to select features.

![BBNCroads](https://github.com/xJKLx/GIS/assets/157556286/235dc5ae-6a74-4f0a-8571-349e7fba1ab4)
![BBNCreduction](https://github.com/xJKLx/GIS/assets/157556286/4ec22439-7cec-42b2-a7b4-925b43043d95)

Satellite images from Landsat 8 Level 2, Collection 2, Tier 1 were extracted from Google Earth Engine (GEE) and cloud-free images were created from three two-year periods 2017-2022 by mosiacking, and exported to Google Drive as GeoTIFF. Surface reflectance bands (B3, B4 and B5) were used to visualise colour infrared vegetation in QGIS.

![BBNCLandsatSR](https://github.com/xJKLx/GIS/assets/157556286/e2a7fcf6-9105-4f7c-b498-c6d929a4f672)

Cloud-free composite Landsat 8 images were used to calculate NDVI for each two-year time periods. Study area is shown by the blue box (left). QGIS was used to reclassify raster pixels with NDVI values greater than 0.7, using raster calculator, and converting raster to vector with Polygonize tool. Vector layer is dissolved to obtain single polygon of natural areas (right).

![BBNCcloudfreendvi](https://github.com/xJKLx/GIS/assets/157556286/7f5bd42f-131e-4aad-b72f-ad1b5981da33)

## Vector manipulation and analysis
To identify connected patches within 100m apart, natural areas are buffered at 50m in QGIS. Roads buffered at 7.5m represent the fragmentation geometry which is subtracted from the buffered natural areas. The result is intersected with the unbuffered natural areas to identify patches that remain connected.

A connectivity analysis is undertaken to study the temporal and spatial changes in natural areas and fragmentation geometry using four scenarios:  <br>
Scenario 1 - With barriers (roads), without connectors. Based on 2017-18 natural areas.  <br>
Scenario 2 - With barriers (roads), without connectors. Based on 2019-20 natural areas.  <br>
Scenario 3 - With barriers (roads), without connectors. Based on 2021-22 natural areas.  <br>
Scenatio 4 - With barriers (roads) and connectors. Based on 2021-22 natural areas.

![BBNCconnectedisolated](https://github.com/xJKLx/GIS/assets/157556286/3016ca60-eefc-4838-9f67-e3a46c9da777)

Total connectivity increased by 1.62km2 (4.3%) from the removal of road barriers due to the BBNC connectors, keeping the natural areas constant in Scenarios 3 and 4 (without and with connectors, respectively). Total connectivity in Scenario 4 is greater than Scenario 1 (without connectors) although the total area of natural areas decreased over the time period by 1.97km2 (5.2%).

Patch analysis conducted showed that BBNC connectors reduced the number of patches and there was a corresponding increase in average patch size between Scenarios 4 and 3. The change in fragmentation geometry from removal of barriers resulted in higher intra-patch and inter-patch connectivity. Increase in inter-patch connectivity contributed more to the increase in total connectivity, indicating that the connectors significantly increased connected patches in the landscape.

In summary, the findings of the study support the implementation of greenways in increasing connectivity of fragmented natural areas in urban landscapes, compensating for loss of natural areas. Further, small patches by themselves do not contribute significantly to total connectivity but there are significant gains by connecting patches to larger patches with the removal of barriers.

[Return to Projects List](https://github.com/xJKLx/GIS?tab=readme-ov-file#projects-list)

# Spatial Analytics

## Modelling Spatial Dependency of Dengue Transmission in Singapore

*Overview*  <br>

Spatial modelling has been used in epidemiology to describe existing and predict future disease occurrence. This project undertook a spatial analysis of dengue transmisison in Singapore on the study date of 28 June 2023. The study aims to describe the spatial distribution of dengue on the study date and attempts to identify a spatial process in place that explains the spread of dengue.

Data on dengue clusters including case sizes tracked by the National Environment Agency (NEA) was obtained for the date 28 June 2023 using OneMap API  and python wrapper client onemapsg 1.0.3. The spatial distribution and intensity of dengue clusters was mapped to examine potential spatial dependence and patterns of spatial clustering. The polygons of dengue clusters were plotted by using geopandas to read the data as a GeoDataFrame in Jupyter Notebook. Dengue clusters polygons were rasterized in QGIS and cluster size (column = “case _size”) values were burned into raster cells to generate a zonal map together with the planning subzone boundaries shapefile. 

![Dengueclusterzonal](https://github.com/xJKLx/GIS/assets/157556286/0ee549c3-ed89-4825-bdaa-1d7363f905e9)

The skewed dataset with low mean case size (8.61) and a single extraordinarily high dengue case size (187) accounting for more than 60% of the total cases implied high spatial heterogeneity but complicated statistical analysis for non-randomness.

A series of experiments on spatial weight matrices was conducted with both contiguity and distance-based models. 

![denguespatialweight](https://github.com/xJKLx/GIS/assets/157556286/7029439c-5774-4269-a4f4-7e7e3e674995)

Global Moran’s I metrics were calculated and Moran scatterplots were produced for each model and results were analysed for potential spatial dependency in dengue cluster case sizes. In all the spatial weight matrices the Global Moran’s I values were 0.02 and smaller and there is no significant difference (p<0.05) from a random distribution, so the null hypothesis of spatial randomness cannot be rejected. The k=15 nearest neighbours spatial weight matrix had the lowest p-score and highest z-score, indicating more spatial clustering.

Further investigation on potential spatial dependence in specific regions is conducted with Local Indicators of Spatial Association (LISA).

![denguelocalmoran](https://github.com/xJKLx/GIS/assets/157556286/667fcd46-80d2-4317-bcde-378087b162e5)

The top left plot categorizes the individual Subzones by the Moran’s I value or the degree to which there is positive (HH or LL) or negative (HL or LH) spatial correlation in case sizes. There are more Subzones with positive correlation than negative correlation and the absolute degree of positive correlation is higher than that of negative correlation. However, negative correlation is concentrated in the center where there are most dengue clusters. The top right plot distinguishes the Subzones into the respective four Moran scatterplot quadrants. It is evident that the positively correlated HH quadrant values are in central region around the Subzone with the highest case size of 187 and the (positively correlated) LL quadrant values form a boundary in the outer areas. The bottom left plot shows where the Local Moran’s I statistic is significant or not and the bottom right plot shows the respective quadrant of the statistically significant values. From the former most values are non-significant (256 out of 332), which explains the low Global Moran’s I. From the latter it is observed that the single HH cluster of Subzones (“hotspot”) is surrounded by LH Subzones (“doughnuts”) whereas there is a single HL Subzone (“diamond in the rough”) in the west region, and many LL Subzones in the outer areas (“cold spots”). 

The analysis of local areas at each Subzone level and whether they belong to a statistically significant cluster of Moran scatterplot quadrant type provided a richer picture of spatial dependence over space, which the global measure of spatial autocorrelation with Global Moran’s I cannot capture. The identification of statistically significant local areas of correlated dengue case sizes, particularly the central region “hotspot” and west region “diamond in the rough”, motivates comparison of local conditions and measures that can explain the difference in spatial patterns.  

[Return to Projects List](https://github.com/xJKLx/GIS?tab=readme-ov-file#projects-list)

# GIS Analysis in Building Resilient Settlements

*Overview*  <br>
This project in building resilient settlements explores aquaculture as a nature-based solution in the adaptation of coastal social-ecological systems to climate change. Aquaculture practices in seaweed and shellfish farming can realise potential benefits to ecosystem services including carbon sequestration and nitrogen bio-extraction and nutrient regulation, as well as mitigating eutrophication from agriculture. 

A GIS site analysis integrates environmental and socio-economic factors to assess site suitability in the  local context. Coastal resilience is achieved by aligning aquaculture initiatives with objectives for coastal protection. Aquaculture is an effective NbS coastal defense strategy providing enhanced protection in combination with submerged aquatic vegetation and living shorelines.

Coastkit by the Victoria State Government Environment, Land, Water and Planning Department (DELWP) was used to identify coastal hazard assessment levels. Tbe Werribee South Coast is exposed to medium to high erosion hazards, and very high levels in small sections. 
![Investigation areas werribee](https://github.com/xJKLx/GIS/assets/157556286/bb3efbe8-f361-4323-a6cb-d2b4282b2f9e)

The Werribee South coast off the Intensive Agricultural Precinct is exposed to high levels of Sea Level Rise under the very high inundation scenario in 2150, using data sourced from coastalrisk.com.au.
![2150SLRWerribee](https://github.com/xJKLx/GIS/assets/157556286/4ba6bb77-7ea6-4326-8dcc-0bb319e9c465)

Water quality in the proximity of the Western Treatment Plant (WTP) is an important consideration for ensuring food safety of aquaculture products. The proposal factors this into consideration by applying an exclusion zone to waters suitable for human consumption of aquatic foods, regulated by the Environmental Protection Agency (EPA). Shellfish aquaculture aligns with objectives to improve water quality through nutrient regulation, mitigating the nutrient-rich runoff from the IAP.

There are synergies in aligning aquaculture initiative with biodiversity conservation objectives. In addition to nutrient reduction, shellfish are shown to contribute to well-functioning and resilient marine ecosystems. Naturekit by DELWP was used to identify biodiversity values of agriculture land, surrounding land uses and conservation areas. 
![BiodiversityWerribee](https://github.com/xJKLx/GIS/assets/157556286/c37a494b-4ca6-456b-b494-162894e34a7a)

Coastkit provided marine conservation sites and threatened species protected under state and national legislation.
![Investigation area werribee](https://github.com/xJKLx/GIS/assets/157556286/9fab03fe-054e-4627-975b-ee4eb84abf3d)

This planning solution proposes aquaculture investigation areas off the coast of Werribee South from GIS analysis in relation to surrounding land use, coastal erosion hazards and conservation areas. The recommendation to establish aquaculture of oyster and seaweed aims to derive potential benefits in managing conservation and coastal protection, food security and provide a sustainable source of economic activities. 

[Return to Projects List](https://github.com/xJKLx/GIS?tab=readme-ov-file#projects-list)

# Cartography

## Hiking Map of Wilsons Promontory

A map of the Wilsons Promontory National Park was produced for bushwalkers hiking from Tidal River campground to the lighthouse in the southern section of the National Park. The map extent is zoomed into the southern section of the National Park showing the hike trails, marked with arrows clearly. Campgrounds are shown as well as the amenities on site, such as car parks, toilets and water points. Terrain types, contours, lookouts and important landmarks are indicated. Elevations are rendered to give a sense of the topography and water courses are identified. Symbols and labels are offset so that they do not overlap and appropriate level of detail is shown to highlight important features.

![WilsonsProbush](https://github.com/xJKLx/GIS/assets/157556286/2376f898-6355-431c-973a-ebc25e631c69)

## Bushfire Management Map of Wilsons Promontory

A map of the Wilsons Promontory National Park was produced for biodiversity officer, providing information on vegetation types impacted by burns in fire operations plans. Burn units, including for fuel reduction and ecological purposes, and the Ecological Vegetation Divisions they intersect are indicated clearly with symbology for different classifications. Roads and hiking trails as well as topography are also shown to give indication of location. 

![WilsonsProfire](https://github.com/xJKLx/GIS/assets/157556286/76e152ba-d2ec-4084-885d-ec23c2b5be9a)

[Return to Projects List](https://github.com/xJKLx/GIS?tab=readme-ov-file#projects-list)

## Spatial Patterns of Agglomeration in one-north

*Overview*  <br>
The central role of agglomeration economies was examined in the planned approach and outcomes in the development of one-north, a 200-hectare innovation district in southwestern Singapore. one-north has gained international recognition as a leading state-led technology district, an innovation ecosystem with a mix of retail, civic, cultural, entertainment and lifestyle uses providing an integrated work-live-play-learn environment. 

Visualisation of the eight precincts and specialised hubs show localisation economies in Marshallian clusters of firms in respective industries, as well as urbanisation economies of established multidisciplinary creative regions and co-located corporate services to support firms across sectors. Spatial patterns of intra-cluster, inter-sectoral and inter-district interactions represent the driving forces of agglomeration economies that positioned the industrial district as an innovation ecosystem as part of Singapore’s Technopreneurship 21 (T21) economic strategy to develop high-tech industries.   

![onenorthwlegend](https://github.com/xJKLx/GIS/assets/157556286/38b72ae2-9079-4c6d-b863-f58de7d85260)

[Return to Projects List](https://github.com/xJKLx/GIS?tab=readme-ov-file#projects-list)
