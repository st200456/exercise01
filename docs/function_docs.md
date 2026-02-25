# Documentation of Functions and Custom Classes
This page gives an overview of all the tool’s functions and custom classes, explaining what they do, their input parameters, and the types of data they return.
## Main.py
This script is the main entry point of the terrain-processing workflow. It validates an Area of Interest (AOI), downloads a DEM, aligns landcover data, computes roughness, extracts the thalweg, and generates an elevation profile along the extracted flow path.
The main.py file serves as the entry point of the application.
### Overview
It orchestrates all processing steps by calling the following custom classes:
 - AOI
 - DEMFetcher
 - LandCoverFetcher
 - RoughnessCalculator
 - ThalwegExtractor
 - ProfileSampler

All outputs are saved inside the /data and /results directories.
### AOIValidator Class
A class for validating Area of Interest (AOI) bounding box coordinates before DEM data acquisition.
#### Methods
`__init__(self, west, south, east, north)`

Initializes the AOI validator with bounding box coordinates.
- west (float): Western longitude
- south (float): Southern latitude
- east (float): Eastern longitude
- north (float): Northern latitude
`validate(self)`
Runs validation checks on the coordinates (type, geographic range, and logical order)

Returns: bool indicating whether the AOI is valid

Raises: ValueError if validation fails
`get_bbox(self)`
Returns the bounding box coordinates as a dictionary

Returns: dict containing west, south, east, and north coordinates

## pdfdocument.py
::: pdfdocument
## AOIValidator Class
::: raster
## AOIValidator Class
::: raster
## AOIValidator Class
::: raster
## AOIValidator Class
::: raster
## pdfdocument.py
::: pdfdocument
## pdfdocument.py
::: pdfdocument
## pdfdocument.py
::: pdfdocument
## pdfdocument.py
::: pdfdocument
