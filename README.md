#### NERACOOS Crawler

[NERACOOS](http://neracoos.org/) provides OpeNDAP access to data from within R.  `neracooscrawler` package provides basic THREDDS crawling facilties.  The idea is to programmatically search the OpeNDAP offerings at [NERACOOS](http://www.neracoos.org/thredds/catalog/GMRI/SATELLITE/NASA/catalog.html).  

This package is nearly identical to [obpgcrawler](https://github.com/btupper/obpgcrawler) but is configured specifically for the NERACOOS offerings.  Windows users are able to use the crawler to identify resources, but are unable to use the OpeNDAP services.  To circumvent that issue, this package provides utlitiy functions for downloading files to a local drive.

#### Requirements

[R >= 3.0](http://cran.r-project.org)

[threddscrawler](https://github.com/btupper/threddscrawler)

#### Installation

It is easy to install with [devtools](https://cran.r-project.org/web/packages/devtools/index.html)

```R
library(devtools)
install_github("btupper/neracooscrawler")
```

#### Useage

Most users will only use the `MODISA_query()`. An equivalent `MURSST_query()` is under development.

```r

# get all of the monthly CHL in a 2 year period
x <- MODISA_query(what = 'within', date_filter = as.POSIXct(c("2008-01-01", "2011-12-31")),
    greplargs = list(pattern="MO_CHL_chlor_a_4km", fixed = TRUE))

head(x, n = 2) ; cat("..............\n\n"); tail(x, n = 2)
# $A20080012008031.L3m_MO_CHL_chlor_a_4km.nc
# Reference Class: "DatasetsRefClass"
#   verbose_mode: FALSE
#   url: http://www.neracoos.org/thredds/catalog/GMRI/SATELLITE/NASA/MODISA_NESHELF/MODISA/L3SMI/2008/001/A20080012008031.L3m_MO_CHL_chlor_a_4km.nc
#   children: dataSize date
#   datasets: NA
# 
# $A20080322008060.L3m_MO_CHL_chlor_a_4km.nc
# Reference Class: "DatasetsRefClass"
#   verbose_mode: FALSE
#   url: http://www.neracoos.org/thredds/catalog/GMRI/SATELLITE/NASA/MODISA_NESHELF/MODISA/L3SMI/2008/032/A20080322008060.L3m_MO_CHL_chlor_a_4km.nc
#   children: dataSize date
#   datasets: NA
# 
# ..............
# 
# $A20113052011334.L3m_MO_CHL_chlor_a_4km.nc
# Reference Class: "DatasetsRefClass"
#   verbose_mode: FALSE
#   url: http://www.neracoos.org/thredds/catalog/GMRI/SATELLITE/NASA/MODISA_NESHELF/MODISA/L3SMI/2011/305/A20113052011334.L3m_MO_CHL_chlor_a_4km.nc
#   children: dataSize date
#   datasets: NA
# 
# $A20113352011365.L3m_MO_CHL_chlor_a_4km.nc
# Reference Class: "DatasetsRefClass"
#   verbose_mode: FALSE
#   url: http://www.neracoos.org/thredds/catalog/GMRI/SATELLITE/NASA/MODISA_NESHELF/MODISA/L3SMI/2011/335/A20113352011365.L3m_MO_CHL_chlor_a_4km.nc
#   children: dataSize date
#   datasets: NA
```

For Windows users who cannot access OpeNDAP resources, we provide a download function.  Taking the example above we can download on or more of these datasets.

```r

ok <- MODISA_download(x[1:3], dest = "/Users/ben/Downloads")
ok
# /Users/ben/Downloads/A20080012008031.L3m_MO_CHL_chlor_a_4km.nc 
#                                                           TRUE 
# /Users/ben/Downloads/A20080322008060.L3m_MO_CHL_chlor_a_4km.nc 
#                                                           TRUE 
# /Users/ben/Downloads/A20080612008091.L3m_MO_CHL_chlor_a_4km.nc 
#                                                           TRUE 
```

