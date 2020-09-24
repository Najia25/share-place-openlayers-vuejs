<template>
  <div class="home">
    <top-bar>Share a Place</top-bar>
    <section id="selected-place">
      <div id="map"></div>
    </section>
    <render-map></render-map>
    <share-place></share-place>
    <find-place></find-place>
  </div>
</template>

<script>
import TopBar from "@/components/layout/TopBar";
import SharePlace from "@/components/SharePlace";
import FindPlace from "@/components/FindPlace";

export default {
  components: {
    TopBar,
    SharePlace,
    FindPlace
  }
};
</script>

<style>
#selected-place {
  width: 40rem;
  height: 25rem;
  max-width: 90%;
  margin: 2rem auto;
  border: 1px solid #ccc;
}
</style>
