# RI ZCTAs
Process for creating a RI specific map of zip code tabluation areas from U.S. Census national ZCTA .shp files

The 2020 ZCTA file provided by the U.S Census Bureau contains data for the entire country. In order to simplify things and work with smaller files this file describes how to use python to create a new set of files containing a subset of the zip codes. In this case an array of RI zip codes were used to filter the data.

The original zip code shp file was downloaded from [The U.S Census Bureau](https://www.census.gov/cgi-bin/geo/shapefiles/index.php?year=2020&layergroup=ZIP+Code+Tabulation+Areas)

# step 1 set up notebook environment
``` python
import geopandas as gp

```
Import the national data

```python
zcta5 = gp.read_file('{./path/to}/tl_rd22_us_zcta520.shp')

```
Set the list of zip codes to keep

```python
zcList = ['02860',  '02895',  '02909',  '02908',  '02920',  '02864',  '02816',  '02907',  '02904',  '02893',  '02886',  '02919',  '02889',  '02861',  '02905',  '02906',  '02840',  '02852',  '02910',  '02879',  '02809',  '02863',  '02891',  '02914',  '02818',  '02888',  '02865',  '02871',  '02806',  '02842',  '02878',  '02911',  '02915',  '02917',  '02882',  '02903',  '02921',  '02896',  '02885',  '02916',  '02813',  '02857',  '02814',  '02859',  '02828',  '02881',  '02874',  '02817',  '02830',  '02822',  '02892',  '02825',  '02835',  '02832',  '02912',  '02831',  '02838',  '02837',  '02918',  '02804',  '02808',  '02827',  '02841',  '02898',  '02839',  '02812',  '02807',  '02833',  '02876',  '02858',  '02826',  '02894',  '02802',  '02875',  '02815',  '02829',  '02836',  '02872',  '02873',  '02823',  '02824']

```

Filter the geopandas dataframe by the list of zip codes

```python
zcta5 = zcta5[zcta5['ZCTA5CE20'].isin(zcList)]

```

Export new layer

```python
zcta5.to_file('{./save/path}/riZipMap')

```
