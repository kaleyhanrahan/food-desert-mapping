library(MASS)
library(RColorBrewer)
library(maptools)

### Plot City Bounday
city.boundary = readShapePoly("City_Boundary/geo_export_8e9e40f9-be43-489a-a8a7-64eb8423712c")

### Plot Grocery Story Locations
groc_full <- read.csv("Map_of_Grocery_Stores_2013.csv")
groc = groc_full[, 15:16]
plot(groc[,2],groc[,1])

##############
## KDE Plot ##
##############
### Color palette for heat map
palette.function = colorRampPalette(rev(brewer.pal(11,'Spectral')))
heat.colors = palette.function(32)

### KDE with default bandwidth (h)
est = kde2d(groc[,2], groc[,1], n=c(1000,1000), lims=c(-87.96,-87.5, 41.63, 42.05))  # h=0.05
image(est, col = heat.colors, useRaster=TRUE, asp=1)
plot(city.boundary, add=TRUE, axes=TRUE, border="black", asp=1)

### Test multiple bandwidths (h)
est = kde2d(groc[,2], groc[,1], h=0.05, n=c(1000,1000), lims=c(-87.96,-87.5, 41.63, 42.05))  # h=0.05
image(est, col = heat.colors, useRaster=TRUE, asp=1)
plot(city.boundary, add=TRUE, axes=TRUE, border="black", asp=1)

est = kde2d(groc[,2], groc[,1], h=0.1, n=c(1000,1000), lims=c(-87.96,-87.5, 41.63, 42.05))  # h=0.1
image(est, col = heat.colors, useRaster=TRUE, asp=1)
plot(city.boundary, add=TRUE, axes=TRUE, border="black", asp=1)

est = kde2d(groc[,2], groc[,1], h=1, n=c(1000,1000), lims=c(-87.96,-87.5, 41.63, 42.05))  # h=1
image(est, col = heat.colors, useRaster=TRUE, asp=1)
plot(city.boundary, add=TRUE, axes=TRUE, border="black", asp=1)

# Bandwidth of h=0.05 looks to be most informative - there are clear areas without grocery stores.

### References
# https://www.r-bloggers.com/shapefiles-in-r/
