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

`_check_logic(self)`

Checks that min/max coordinate order is correct.

- `west < east`

- `south < north`

- Raises: `ValueError` if bounding box order is invalid

`get_bbox(self)`

Returns the bounding box coordinates as a dictionary.

- Returns: dict with keys: `west`, `south`, `east`, `north`

### DemFetcher Class

A class for downloading Digital Elevation Model (DEM) data from the OpenTopography API using the SRTMGL1 dataset.

#### Methods

`__init__(self, api_key=None)`

Initializes the DEM fetcher.

- `api_key` (`str` or `None`): OpenTopography API key for higher request limits

`download(self, south, north, west, east, output_file="dem_wgs84.tif")`

Downloads a DEM GeoTIFF file for the specified bounding box.

- `south` (`float`): Southern latitude boundary

- `north` (`float`): Northern latitude boundary

- `west` (`float`): Western longitude boundary

- `east` (`float`): Eastern longitude boundary

- `output_file` (`str` or `Path`): Output file path for the DEM

Returns: Path to the downloaded DEM file

Raises: Exception if the API request fails

### Landcover Class

A class for matching landcover raster data to the DEM resolution, extent, and coordinate system.

#### Methods

`__init__(self, output_file, output_src, output_landcover_file)`

Initializes the landcover matcher.

- `output_file` (`str` or `Path`): Reference raster file (DEM)

- `output_src` (`str` or `Path`): Source landcover raster

- `output_landcover_file` (`str` or `Path`): Output matched landcover file

`match(self)`

Resamples and aligns the landcover raster to match the DEM projection, extent, and resolution.

Returns: `Path` to the matched landcover raster file

`__str__(self)`

Returns a string description of the matching process.

Returns: `str` describing the input and output raster files

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
