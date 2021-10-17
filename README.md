# RazazaDrianSpill
NDVI, of Razazah Lack showing the spillway of the Karbala Drain.
projects/ee-hydralmaliky/assets/Kirbalah2
COPERNICUS/S2
// Creat a FeatureCollection form Shapfile.   
var KRB = ee.FeatureCollection('users/hydralmaliky/Kirbalah2');
Map.addLayer(KRB);
Map.centerObject(KRB,9);
Map.setCenter(43.89526, 32.69826, 13)

// Add image form Sentinel_2, 13/10/2021. 
var Sen2 = ee.ImageCollection(Raz1);
var KRBimg = ee.Image(Sen2.filterDate("2021-10-1","2021-10-13").
filterBounds(KRB).
sort("CLOUD_COVERAGE_ASSESSMENT").first());

// Display the image of Sentinel-2 on the Shapfile of Karbalah Gov.
print("Sentinel-2 Scene", KRBimg);


var trueColor = {bands: ["B12", "B8A", "B4"], min: 0, max: 3000};
Map.addLayer(KRBimg ,trueColor, "True Color");
