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
## AOIValidator Class
A class for validating `Area of Interest (AOI)` bounding box coordinates before DEM data acquisition.
### Methods
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

## DemFetcher Class

A class for downloading Digital Elevation Model (DEM) data from the OpenTopography API using the SRTMGL1 dataset.

### Methods

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

## Landcover Class

A class for matching landcover raster data to the DEM resolution, extent, and coordinate system.

### Methods

`__init__(self, output_file, output_src, output_landcover_file)`

Initializes the landcover matcher.

- `output_file` (`str` or `Path`): Reference raster file (DEM)

- `output_src` (`str` or `Path`): Source landcover raster

- `output_landcover_file` (`str` or `Path`): Output matched landcover file

`match(self)`

Resamples and aligns the landcover raster to match the DEM projection, extent, and resolution.

- Returns: `Path` to the matched landcover raster file

`__str__(self)`

Returns a string description of the matching process.

- Returns: `str` describing the input and output raster files

## Roughness Class

A class for computing a Manning’s n roughness raster from landcover data.

### Methods
`__init__(self, landcover_file, out_file)`

Initializes the roughness calculation.

- `landcover_file`: Input landcover raster file

- `out_file`: Output roughness raster file

`compute(self)`

Generates a roughness raster by mapping landcover classes to Manning’s n coefficients.

- Returns: Path to the generated roughness raster file

- Raises: RuntimeError if the landcover raster cannot be opened

`__str__(self)`

Returns a string description of the roughness computation.

- Returns: str describing the input and output raster files

## ThalwegExtractor Class

A class for extracting the main channel (thalweg) from a Digital Elevation Model (DEM).

### Methods
`__init__(self, dem_file, output_vector="Thalweg.shp", threshold=1000, outlet_coords=None)`

Initializes the thalweg extraction.

- `dem_file`: Input DEM raster file

- `output_vector`: Output shapefile path

- `threshold`: Minimum flow accumulation threshold

- `outlet_coords`: Outlet coordinates in DEM CRS

`compute(self)`

Runs the full thalweg extraction workflow (hydrology computation, outlet detection, tracing, and export).

- Returns: Path to the generated shapefile, or None if extraction fails

`_compute_hydrology(self)`

Computes flow direction and flow accumulation from the DEM.

- Returns: Grid object, DEM raster, flow direction array, and flow accumulation array

`_get_outlet(self, flow_acc, dem)`

Determines the outlet cell used as the starting point for tracing.

- Returns: Tuple (row, col) representing the outlet cell

`_trace_thalweg(self, flow_dir, flow_acc, dem, outlet)`

Traces the upstream flow path based on maximum accumulation.

- Returns: LineString geometry of the thalweg, or None if too short

`_export_vector(self, line, dem)`

Exports the extracted thalweg as a shapefile.

- Returns: Path to the saved shapefile

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
