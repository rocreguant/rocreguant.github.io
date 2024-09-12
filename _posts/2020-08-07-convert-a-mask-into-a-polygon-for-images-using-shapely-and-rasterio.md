---
title: "Convert a mask into a Polygon for images using shapely and rasterio"
date: "2020-08-07"
categories: 
  - "programming"
tags: 
  - "images"
  - "mask"
  - "polygon"
  - "raster"
  - "rasterio"
  - "shapely"
---

Sometimes it is necessary to transform masks into polygons to use polygon operations. The way to transform a raster or a binary mask into a polygon is pretty easy. Most of the solutions I found online were the other way (from polygon to a mask). But for my project I needed to convert the mask to a polygon.

<script src="https://gist.github.com/rocreguant/4a2e1b762917bd2b80915403f66dcc3a.js"></script>
