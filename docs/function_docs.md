# Documentation of Functions and Custom Classes
This page gives an overview of all the tool’s functions and custom classes, explaining what they do, their input parameters, and the types of data they return.
## Main.py
This script is the main entry point of the terrain-processing workflow. It validates an Area of Interest (AOI), downloads a DEM, aligns landcover data, computes roughness, extracts the thalweg, and generates an elevation profile along the extracted flow path.
The `Main.py` file serves as the entry point of the application.
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
A class for validating `Area of Interest (AOI)` bounding box coordinates before DEM data acquisition.
#### Methods
`__init__(self, west, south, east, north)`

Initializes the AOI validator with bounding box coordinates.
- `west` (`float`): Western longitude
- `south` (`float`): Southern latitude
- `east` (`float`): Eastern longitude
- `north` (`float`): Northern latitude
  
`validate(self)`

Runs all verification checks (type, range, and logical order).

- Returns: `bool` (`True` if valid)

- Raises: `ValueError` if validation fails

`_check_types(self)`

Checks that all inputs are numeric (`int` or `float`).

- Raises: `ValueError` if any coordinate is not numeric

`_check_ranges(self)`

Checks that coordinates fall within valid WGS84 ranges.

- Longitude must be between `-180` and `180`

- Latitude must be between `-90` and `90`

- Raises: `ValueError` if out of range

_check_logic(self)

Checks that min/max coordinate order is correct.

- `west < east`

- `south < north`

- Raises: `ValueError` if bounding box order is invalid

get_bbox(self)

Returns the bounding box coordinates as a dictionary.

- Returns: dict with keys: `west`, `south`, `east`, `north`

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
