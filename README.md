# Project Overview

This repository provides the code for data extraction supporting the project on “hierarchical road network generation for smart cities”.

The objective of the project is to develop an explainable, rule-based framework for generating primary, secondary, and connector road networks directly from spatial data, while avoiding heavy reliance on data and black-box learning models. The approach emphasizes reproducibility, modularity, and user control over network structure.

## Overview of the Pipeline

The data preparation process consists of the following steps:

1. Querying OpenStreetMap features using "OSMnx"
2. Clipping spatial features to the administrative boundary
3. Rasterizing the urban layout into an image representation
4. Defining user-controlled network nodes
5. Saving the output and metadata for reproducibility

## What We Used

To transform the open map data to a static image, we use a set of specialized libraries:

- OSMnx queries and downloads the relevant urban features from OpenStreetMap.
- GeoPandas processes the spatial data and clips it precisely to Carouge’s boundaries.
- Shapely handles the underlying geometric operations.
- Matplotlib helps us visualize the results at each stage.

## The Data We Collected  
(Using `ox.features_from_place(place_name, tags)`)

We extracted key layers that define Carouge’s urban fabric to understand the context in which the road network exists. This includes:

- The city’s official administrative boundary.
- Building footprints across the city.

## Network Nodes (User-Defined and Flexible)

Network nodes represent points of interest that the generated road network must connect.

### Key properties of node placement:

- Nodes are user-defined and not restricted to OSM-provided nodes
- Nodes may represent entry points, exits, transport hubs, intersections, or planning anchors
- Nodes can be placed anywhere within or near the study area
- Nodes falling outside the administrative boundary are automatically projected to the nearest boundary point