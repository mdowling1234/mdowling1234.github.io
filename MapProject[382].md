---
title: "R Markdown and Leaflet Assignment"
output: html_document
author: Michael
date: December 09, 2020
---

```{r}
library("leaflet")
setwd("C:/Users/17244/Documents/R/CourseEra")

National <- read.delim("National.txt")

National <- data.frame(lat = National$Latitude,
                       lng = National$Longitude,
                       popup = National$Place.Name)

NP_icon <- makeIcon(
  iconUrl = "https://upload.wikimedia.org/wikipedia/commons/1/1d/US-NationalParkService-Logo.svg",
  iconWidth = 31*215/230, iconHeight = 45,
  iconAnchorX = 31*215/230/2, iconAnchorY = 16
)



project_map <- National %>%
leaflet() %>%
addTiles() %>%
addMarkers(clusterOptions = markerClusterOptions(), 
           popup = National$popup, icon = NP_icon)

#The map shows locations of National Parks in the United States.
                                            
project_map

```   
