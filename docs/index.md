---
theme: dashboard
toc: true
---

<style>

.hero {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: var(--sans-serif);
  margin: 4rem 0 8rem;
  text-wrap: balance;
  text-align: center;
}

.hero h1 {
  margin: 2rem 0;
  max-width: none;
  font-size: 14vw;
  font-weight: 900;
  line-height: 1;
  background: linear-gradient(30deg, var(--theme-foreground-focus), currentColor);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero h2 {
  margin: 0;
  max-width: 34em;
  font-size: 20px;
  font-style: initial;
  font-weight: 500;
  line-height: 1.5;
  color: var(--theme-foreground-muted);
}

@media (min-width: 640px) {
  .hero h1 {
    font-size: 90px;
  }
}

</style>

<div class="hero">
  <h1>TU/USGS imagery collaboration</h1>
  <h2>This doucment is a guide to the imagery study in the Deerfield River watershed.</h2>
</div>

## Get ready

   
Download [onWater](www.onwaterapp.com) on your phone.

1) Create account 
2) Allow location within the application:
3) Make sure you turn on geolocation of images-

<div class="tip" style="max-width: 740px;">

    On iPhone:  
      Settings -> Privacy and Security -> LocationServices -> Camera Application 

    On android:   
      Settings -> secutity and privacy -> permission manager -> location [allow] 
      Settings -> secutity and privacy -> permission manager -> camera [allow] 

</div>

 The service we need in onWater is FREE. Ignore option to pay to upgrade. (hit “x” in the top right corner) 

<div class="note">
  Image below is not loading for unkonwn reason.
</div>

![image](./docs/images/onW.png)
<img src="./docs/images/onW.png">

## Map of the study areas
There are two regions of interest,  
  1) The Deerfield River **mainstem** from Carbis Bend to the Hoosic tunnel bridge.  
  2) **Blue lines**  
    a) Mill brook, Charlemont along route 8a  
    b) Bear river, from the confluence with the Deerfield

<div class="note">
  Will add flowlines for the study areas.
</div>

```js

  const lat1 = 42.67;
  const lon1 = -72.87;
  const mag1 = 12;

  const div_map1 = display(document.createElement("div"));
  div_map1.style = "height: 400px;";

  const map1 = L.map(div_map1)
    .setView([lat1, lon1], mag1);

  L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>'
  })
  .addTo(map1);

  const basemaps1 = {
    StreetView: L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',   {attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'}),
    Topography: L.tileLayer.wms('http://ows.mundialis.de/services/service?',   {layers: 'TOPO-WMS'}),
    Places: L.tileLayer.wms('http://ows.mundialis.de/services/service?', {layers: 'OSM-Overlay-WMS'}),
    USGS_USImagery: L.tileLayer(
    'https://basemap.nationalmap.gov/arcgis/rest/services/USGSImageryOnly/MapServer/tile/{z}/{y}/{x}',
    {
      maxZoom: 20,
      attribution:
        'Tiles courtesy of the <a href="https://usgs.gov/">U.S. Geological Survey</a>',
    }
  )
  };
  L.control.layers(basemaps1).addTo(map1);
  basemaps1.StreetView.addTo(map1);
```

```js

  const lat2 = 42.618101;
  const lon2 = -72.791500;
  const mag2 = 11;

  const div_map2 = display(document.createElement("div"));
  div_map2.style = "height: 400px;";

  const map2 = L.map(div_map2)
    .setView([lat2, lon2], mag2);

  L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>'
  })
  .addTo(map2);

  const basemaps2 = {
    StreetView: L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',   {attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'}),
    Topography: L.tileLayer.wms('http://ows.mundialis.de/services/service?',   {layers: 'TOPO-WMS'}),
    Places: L.tileLayer.wms('http://ows.mundialis.de/services/service?', {layers: 'OSM-Overlay-WMS'}),
    USGS_USImagery: L.tileLayer(
    'https://basemap.nationalmap.gov/arcgis/rest/services/USGSImageryOnly/MapServer/tile/{z}/{y}/{x}',
    {
      maxZoom: 20,
      attribution:
        'Tiles courtesy of the <a href="https://usgs.gov/">U.S. Geological Survey</a>',
    }
  )
  };
  L.control.layers(basemaps2).addTo(map2);
  basemaps2.StreetView.addTo(map2);
```

<div class="grid grid-cols-2">
  <div class="card">
    <h1> Mainstem </h1>
    ${display(div_map1)}
  </div>
  <div class="card">
    <h1> Blue lines </h1>
    ${display(div_map2)}
  </div>
</div>

## Fish capture

- Keep them wet and minimize handling. If your shot is out of the water, do not exceed 5 seconds out of water. 

- Make sure your hands are wet. 

- Use barbless hooks and rubberized (silicone) nets. 

- If water temp is above 68 F, please do not fish. 

- Record temperature and note the temperature in onWater 

- Record start and end times to add as a onWater journal entry. OnWater may add this feature automatically and may add the GPS track for your fishing bout. 

## Take an image
Two possibilities:
1. Take images and upload to onWater later 

2. Use onWater in journal mode and take the picture from within onWater. This is also good for taking notes and making sure you don't forget to upload images later :)

- *What*: take a picture of the **left** flank of the fish in the net. Only one photo angle is necessary, but extra images do not hurt. Extra images can also be of the right side of the fish, but we will only use the left flank for individual idntification.
 - *Where*: for now, fish randomly within study area, but it is also OK to include pictures from outside of the set study area (any fish picture from any stream is a helpful fish picture!). 

- *How*: try to minimize **glare** in the image as much as possible (you may need to remove polarized glasses – if you want you could also try a polarizing filter for your phone – we don’t know much about this, but there are filters available online...). Also, try to avoid dark images in **shadow**.  
Attempt to capture the full length of the fish and avoid thumbs and fingers in the shot. 

Add comments to note section in onWater.  
  Examples include:
  - relative flow rate  
  - water temperature 
  - air temperature 
  - the fly used
  - condition of the fish 
  - how hard it fought 
  - any scars? describe them 


 One possiblity if you really want to get the perfect image is to turn on forward-facing camera, start recording video and lift the fish into the frame. Images can be extracted later and uploaded to onWater. 

## Upload the image
1. Use onWater in journal mode and take the picture from within onWater.  
You are done.

2. Take images and upload to onWater later  
From Matt: "I recommend taking the photo and then uploading into the app later when you are off the water. After you upload the photo the app will populate with weather and flow information if it is able.  
First step is to open the OnWater app. I hit the X on the upper right hand corner of any pop ups that are asking me to upgrade my membership so that it brings me to the home page which should be a map of your location.  
Next I select the Journal tab in the lower left corner of the app screen and then I select the camera icon and then select "image". This brings you to your camera roll where you can select the photo you want to upload. Once selected you will have the chance to fill in any details about the photo. Then select "Save" in the upper right hand corner. Afterwards you can re open the photo and see if any of the extra data has been populated."  



## Verify identities
This is in progress. WildMe will provide probabilities of **individual identity** for each submitted image. Users will verify the identity based on angler's experience with the fish and the current image and based on the images for the verified identies of previously-caught fish.
