<template>
  <div class="my-place">
    <top-bar>{{ address }}</top-bar>
    <render-map :mapData="mapData"></render-map>
    <section id="share-controls">
      <a href="/">Share a New Place!</a>
    </section>
  </div>
</template>

<script>
import RenderMap from "@/components/RenderMap";
import TopBar from "@/components/layout/TopBar";
export default {
  components: {
    TopBar,
    RenderMap
  },
  data() {
    return {
      address: "",
      mapData: {
        coordinates: {
          lat: 0,
          long: 0
        }
      }
    };
  },
  created() {
    this.address = decodeURI(this.$route.params.address);
    /* eslint-disable no-undef */
    // eventBus.$emit("gotAddressAndCoords", {
    //   coordinates: {
    //     lat: this.$route.params.lat,
    //     long: this.$route.params.long
    //   }
    // });
    (this.mapData.coordinates.lat = this.$route.params.lat),
      (this.mapData.coordinates.long = this.$route.params.long);
  }
};
</script>
<style>
#share-controls a {
  text-decoration: none;
  font-size: 1.25rem;
  background: #36007c;
  color: white;
  border: 1px solid #36007c;
  border-radius: 6px;
  padding: 0.5rem 1.5rem;
  margin: 0.5rem 0;
  cursor: pointer;
}

#share-controls a:focus {
  outline: none;
}

#share-controls a:hover,
#share-controls a:active {
  background: #55007c;
  border-color: #55007c;
}
</style>
