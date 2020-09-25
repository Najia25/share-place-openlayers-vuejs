<template>
  <section id="place-data">
    <form>
      <label for="address">Address</label>
      <input type="text" />
      <button type="submit">Find Place</button>
    </form>
    <button id="locate-btn" @click="locareUserHandler">
      Get Current Location
    </button>
    <modal v-if="loading"></modal>
  </section>
</template>

<script>
import { getAddressFromCoords } from "@/utility/Location";

export default {
  name: "find-place",
  components: {
    Modal: () => import("@/components/Modal")
  },
  data() {
    return {
      loading: false
    };
  },
  methods: {
    locareUserHandler() {
      if (!navigator.geolocation) {
        alert("Sorry! location feature is not available in your browser!");
        return;
      }
      this.loading = true;
      navigator.geolocation.getCurrentPosition(
        async result => {
          const coordinates = {
            lat: result.coords.latitude,
            long: result.coords.longitude
          };
          console.log(coordinates);
          const address = await getAddressFromCoords(coordinates);
          this.loading = false;
          // this.selectPlace(coordinates, address);
          /* eslint-disable no-undef */
          eventBus.$emit("gotAddressAndCoords", {
            coordinates,
            address
          });
        },
        () => {
          this.loading = false;
          console.log("Could not locate you! please enter address manually");
        }
      );
    }
  }
};
</script>

<style lang="scss" scoped>
#place-data {
  width: 40rem;
  max-width: 90%;
  margin: 2rem auto;
  border: 1px solid #ccc;
  padding: 1rem;
  text-align: center;
}
</style>
