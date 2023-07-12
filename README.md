# Palau-Graphics
Plots and Graphs for Palau

#Precipitation
  Description:
    Uses Pacific Climate Change Data Portal, Australia BOM rainfall data and creates graph for rainfall and number of wet days (with ENSO labels)
      http://www.bom.gov.au/climate/pccsp/

  Files:
    PLW_000001_Rain.csv
      CSV from Pacific Climate Change Data Portal Australia Bureau of Meteorology Rainfall data (monthly)
    PLW_000001_Rain_daily.csv
      CSV from Pacific Climate Change Data Portal Australia Bureau of Meteorology Rainfall data (daily)
    PalauPrecipitation.ipynb
      Uses both rainfall csv and creates graph for rainfall and number of wet days (with ENSO labels)
      
#PACCSAP-wave

  Description:
    Downloads, processes, and creates geojson contour plots for wave height from Pacific-Australia Climate Change Science and Adaptation Planning Program (PACCSAP)
    wave hindcast data. Also, creates geojson files for wave direction in the form of arrows. Both geojson files formatted to be used with DeckGL.
    
  Files:
    downloadPACCSAP.ipynb
      Downloads all current PACCSAP (up to 2023) .nc file and saves it to a folder.
    processPACCSAP.ipynb
      Converts .nc files into python dataframe saved as pickle and csv files. Filters specifically to Palau EEZ. Also can create averages over intervals (e.g. average every three months).
    contourPACCSAP.ipynb
      Creates geojson contour plots for wave height and geojson files for wave direction in the form of arrows from pickle files created from processPACCSAP.ipynb
  Instructions:
    Run downloadPACCSAP.ipynb, then processPACCSAP.ipynb, then contourPACCSAP.ipynb
