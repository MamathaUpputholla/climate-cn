# Load in the tidyverse, raster, and sf packages
library(tidyverse)
library('sf', 'raster')


# Read the climate data from an rds file
climate  <- read_rds('datasets/climate_raster.rds')

# Have a look at the variables in the climate data
colnames(climate)

# Convert to SpatialPixelDataFrame for plotting
climate_df <- mutate(
  .data = climate, 
  rasters = map(
    .x = rasters, 
    ~ as_tibble(as(.x, "SpatialPixelsDataFrame")))) %>%
  unnest()# climate-cn
