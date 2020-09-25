<template>
  <section id="selected-place">
    <div id="map"></div>
  </section>
</template>

<script>
import { Map, View } from "ol";
import TileLayer from "ol/layer/Tile";
import VectorLayer from "ol/layer/Vector";
import VectorSource from "ol/source/Vector";
import OSM from "ol/source/OSM";
import Feature from "ol/Feature";
import Point from "ol/geom/Point";
import { Circle as CircleStyle, Fill, Stroke, Style } from "ol/style";
import { fromLonLat } from "ol/proj";

export default {
  name: "render-map",
  data() {
    return {
      map: null
    };
  },
  created() {
    /* eslint-disable no-undef */
    eventBus.$on("gotAddressAndCoords", data => this.renderMap(data));
  },
  methods: {
    renderMap(data) {
      const long = +data.coordinates.long.toFixed(2);
      const lat = +data.coordinates.lat.toFixed(2);
      /* eslint-disable no-debugger */
      debugger;

      const iconGeometry = new Point(fromLonLat([long, lat]));

      const iconFeature = new Feature({
        geometry: iconGeometry
      });

      const source = new VectorSource({
        features: [iconFeature]
      });

      const view = new View({
        center: fromLonLat([long, lat]),
        zoom: 16
      });
      const style = new Style({
        image: new CircleStyle({
          radius: 8,
          fill: new Fill({
            color: "rgba(255, 255, 255, 0.6)"
          }),
          stroke: new Stroke({
            color: "#FF0000",
            width: 2
          })
        })
      });

      iconFeature.setStyle(style);

      const vectorLayer = new VectorLayer({
        source: source
      });

      if (this.map) {
        this.map.getView().setCenter(fromLonLat([long, lat]));
        this.map.getView().setZoom(16);
        this.map.addLayer(vectorLayer);
      } else {
        this.map = new Map({
          target: "map",
          layers: [
            new TileLayer({
              source: new OSM()
            }),
            vectorLayer
          ],
          view
        });
      }
    }
  }
};
</script>

<style>
@import "https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.4.3/css/ol.css";

#selected-place {
  width: 40rem;
  height: 25rem;
  max-width: 90%;
  margin: 2rem auto;
  border: 1px solid #ccc;
}
#map {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
