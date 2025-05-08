````bash
library(tidyverse)
library(readr)

df <- read_delim("C:/Users/Rauno/Desktop/ALGDATA_DogBit_1.csv", delim=";")

df <- df %>%
  filter(!is.na(lat) & !is.na(lon))
install.packages("leaflet")
library(leaflet)

df <- df %>%
  mutate(
    lat = as.numeric(lat),
    lon = as.numeric(lon)
  ) %>%
  filter(!is.na(lat) & !is.na(lon))


leaflet(data = df) %>%
  addTiles() %>%  # Lisab OpenStreetMap taustakaardi
  addCircleMarkers(~lon, ~lat,
                   radius = 2,
                   color = "blue",
                   fillOpacity = 0.5)
install.packages("htmlwidgets")

# Lae vajalikud paketid
library(leaflet)
library(htmlwidgets)
library(tidyverse)

# Loo kaart ja salvesta see objekti 'm'
m <- leaflet(data = df) %>%
  addTiles() %>%
  addCircleMarkers(~lon, ~lat,
                   radius = 2,
                   color = "blue",
                   fillOpacity = 0.5) %>%
  setView(lng = -74.0059, lat = 40.7128, zoom = 11)

# Salvesta kaart interaktiivse HTML-failina
saveWidget(m, "NYC_map.html", selfcontained = TRUE)

getwd()
````
