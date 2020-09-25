<template>
  <div class="home">
    <top-bar>Share a Place</top-bar>
    <render-map></render-map>
    <share-place></share-place>
    <find-place></find-place>
  </div>
</template>

<script>
import TopBar from "@/components/layout/TopBar";
import SharePlace from "@/components/SharePlace";
import FindPlace from "@/components/FindPlace";
import RenderMap from "@/components/RenderMap";

export default {
  components: {
    TopBar,
    SharePlace,
    FindPlace,
    RenderMap
  }
};
</script>
