# share-place-openlayers-vuejs

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

=> The app uses Geolocation API to fetch the users current location.  
=> Upon getting the user coordinates a sharable link is generated, a loading modal is visible and the location is then shown in the map.  
=> I have used OpenLayers library along with OpenStreetMap to render the map.  
=> Clicking on the share button copies the link to the clipboard using clipboard API.  
=> Pasting the copied link in browser address bar shows a different view with the map rendered and the formatted address in the top bar.  
=> Clicking the share new button redirects the user to the home page.  
=> The same procedure repeats for a custom address that user can input in the input field.  
