#### NERACOOS Crawler

[NERACOOS](http://neracoos.org/) provides OpeNDAP access to data from within R.  `neracooscrawler` package provides basic THREDDS crawling facilties.  The idea is to programmatically search the OpeNDAP offerings at [NERACOOS](http://www.neracoos.org/thredds/catalog/GMRI/SATELLITE/NASA/catalog.html).  

This package is nearly identical to [obpgcrawler](https://github.com/btupper/obpgcrawler) but is configured specifically for the NERACOOS offerings.  Windows users are able to use the crawler to identify resources, but are unable to use the OpeNDAP services.  To circumvent that issue, this package provides utlitiy functions for downloading files to a local drive.


The above examples use the simple function, `obpg_query()`.  At the very end of this document is a description of detailed step-by-step process hidden in `obpg_query()`.

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

Most users will only use the `MODISA_query()` and an equivalent `MURSST_query()` is under development.

