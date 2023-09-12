# Palau-Graphics

**Chapter 3 - Rainfall**

**Indicator 3.1: Total Wet Days**

Total wet days with ENSO label
![alt text](<Chapter 3 - Rainfall/vis/Precipitation/graphs/WetDaysMonthlyENSOLabeled.png>)


**Indicator: Monthly Rainfall**

Monthly Total Rainfall
![alt text](<Chapter 3 - Rainfall/vis/Precipitation/graphs/MonthlyRainfall_monthlydata.png>)

**Chapter 7 - Biochemistry**

**7.2 Indicator: Chlorophyll Concentration**

Phytoplankton are the foundation of the marine food web. Their abundance affects food availability for
all consumers, ranging from zooplankton to apex predators. Chlorophyll concentration is used as a proxy
for phytoplankton abundance. Some climate change projections suggest a shift towards lower
phytoplankton abundances, particularly in the ocean’s oligotrophic gyres. Chlorophyll concentration
(and phytoplankton abundance) varies greatly across the Pacific basin, with higher concentrations
generally found at higher latitudes and particularly around coastlines. Chlorophyll concentrations also
vary in response to natural climate variability.
Chlorophyll-a concentration is estimated from satellite remotely sensed observations of ocean color,
which extend back to 1998. The basin-wide average (1998 – 2021) is shown below. The Palau EEZ is also
highlighted as a spatial average (1998 – 2021) and a time series averaged over this area. No significant
trend in chlorophyll concentration was detected over this region and time span.

![alt text](<Chapter 7 - Biochemistry/vis/Chapter 7.2-7.3 Code/output/chlor_con.png>)
![alt text](<Chapter 7 - Biochemistry/vis/Chapter 7.2-7.3 Code/output/chlor_con_report_year_log.png>)

**7.3 Indicator: Estimated Phytoplankton Size**

Phytoplankton size provides insight into ecosystem productivity with larger phytoplankton generally
supporting more productive ecosystems with larger fish. Some climate change projections suggest a
shift towards smaller phytoplankton, particularly in the ocean’s oligotrophic gyres, potentially reducing
food available to all trophic levels. Phytoplankton size varies greatly across the Pacific basin, with larger
phytoplankton generally found at higher latitudes and closer to coastlines.
Phytoplankton size also varies with natural climate cycles such as ENSO, with larger phytoplankton more
prevalent across the equatorial Pacific during cooler La Niña periods and vice versa during El Niño.
Estimated median phytoplankton size can be derived from satellite remotely sensed sea surface
temperature and chlorophyll-a concentration. The basin-wide average (1998 – 2021) is shown below.
The Palau EEZ is also highlighted as a spatial average (1998 – 2021) and a time series averaged over this
area. A statistically significant (p &lt; 0.05) decline in estimated median phytoplankton size was detected
over this area. From 1998 through 2022, estimated median phytoplankton size declined by 0.031 m
Equivalent Spherical Diameter (ESD).

![alt text](<Chapter 7 - Biochemistry/vis/Chapter 7.2-7.3 Code/output/phyto_size.png>)
![alt text](<Chapter 7 - Biochemistry/vis/Chapter 7.2-7.3 Code/output/phyto_size_current_year.png>)




# Folders

## Copernicus-Sea-Level
#### Description:
  Compiles sea level gridded data from Copernicus and creates gridded geoJSON files visualizing it for DeckGL
  ### Files:
  #### cleanAltimetry.ipynb
  > Merges all Copernicus .nc files together and filters data based on a box around Palau's EEZ. Also contains legacy code creating Folium contour plots and HTML line plots and trend lines for sea level rise.
  #### geojsonAltimetry.ipynb
  > Creates gridded geoJSON visualization for sea level formatted for DeckGL
### TO DO:
  > Write script to automate Copernicus sea level download. Change color format of geoJSON.
### Instructions:
  Download Copernicus data, run cleanAltimetry (only first section needed for geoJSON) run geojsonAltimetry.ipynb

## CFS-CRW
  ### Description:
  Downloads Climate Forecast System and Coral Reef Watch data and reformats data into csv and pickle files, with varying temporal averages, used to create Voronoi diagrams (geojson files)
  ### Files:
  #### downloadERDDAP.ipynb
  > Downloads CFS and CRW .nc files in chunks to not be denied access due to large file size inquiry
  #### cleanERDDAP.ipynb
  > Compiles CFS and CRW .nc files into singular csv and pickle files, with ability to reduce dataframe size by creating average over weeks or months.
  #### geojsonERDDAP.ipynb
  > Creates Voronoi diagrams from pickle DataFrames in geoJSON format.
### TO DO:
  > Determine way to visualize Heat wave and Coral Bleaching Alert over spans longer than a week.
### Instructions:
  Run downloadERDDAP.ipynb, then cleanERDDAP.ipynb, then geojsonERDDAP.ipynb

## CMIP6
  ### Description:
  Uses CMIP6 Climate projection model data to create projected plots and geojson Voronoi plots for climate variables.\
  https://esgf-data.dkrz.de/search/cmip6-dkrz/

  ### Files:
   #### get folder
   > wget script to download all relevant climate variables from selected experiment and resolution. I recommend simply making a one line bash script to run all scripts back to back.
   #### tos_palau.ipynb
   > Takes all .nc files downloaded by wget script and filters them to be specific to Palau's EEZ. Organizes by experiment and organization and also creates averaged DataFrame pickle files and csv.
  #### tos_graphic.ipynb
   > Takes DataFrame pickle file screated from tos_palau.ipynb and creates Voronoi diagrams in Geojson files colored by temperature with a corresponding colobar.
### TO DO:
> Create image files for the Voronoi diagrams and save colorbar as image.
### Instructions:
  Run wget scripts to download files, process with tos_palau.ipynb and produce Voronoi diagrams and colorbars for surface temperature.
## Precipitation
  ### Description:
  Uses Pacific Climate Change Data Portal, Australia BOM rainfall data and creates graph for rainfall and number of wet days (with ENSO labels)\
      http://www.bom.gov.au/climate/pccsp/

  ### Files:
  #### PLW_000001_Rain.csv
  > CSV from Pacific Climate Change Data Portal Australia Bureau of Meteorology Rainfall data (monthly)
  #### PLW_000001_Rain_daily.csv
  > CSV from Pacific Climate Change Data Portal Australia Bureau of Meteorology Rainfall data (daily)
  #### PalauPrecipitation.ipynb
  > Uses both rainfall csv and creates graph (.png) for rainfall and number of wet days (with ENSO labels)
      
## PACCSAP-wave

  ### Description:
  Downloads, processes, and creates geojson contour plots for wave height from Pacific-Australia Climate Change Science and Adaptation Planning Program (PACCSAP)
  wave hindcast data. Also, creates geojson files for wave direction in the form of arrows. Both geojson files formatted to be used with DeckGL.
    
  ### Files:
  #### downloadPACCSAP.ipynb
  > Downloads all current PACCSAP (up to 2023) .nc file and saves it to a folder.
  #### processPACCSAP.ipynb
  > Converts .nc files into python dataframe saved as pickle and csv files. Filters specifically to Palau EEZ. Also can create averages over intervals (e.g. average every three months).
  #### contourPACCSAP.ipynb
  > Creates geojson contour plots for wave height and geojson files for wave direction in the form of arrows from pickle files created from processPACCSAP.ipynb
  ### TO DO:
  > Create image files for the contour plots and save colorbar as image. Create Voronoi diagrams in addition to contour plots
  ### Instructions:
  Run downloadPACCSAP.ipynb, then processPACCSAP.ipynb, then contourPACCSAP.ipynb

# Miscellaneous Files
## borderOutlines.ipynb
  Creates a geojson file that is a Polygon (rectangle) containing the entire EEZ of Palau

## palauEEZ.geojson
  geojson containing Multipolygon of the EEZ of Palau. May need to change pathing of certain file for methods like palau_eez in some notebooks.
