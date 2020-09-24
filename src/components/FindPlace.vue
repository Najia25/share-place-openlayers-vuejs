<template>
  <section id="place-data">
    <form>
      <label for="address">Address</label>
      <input type="text" />
      <button type="submit">Find Place</button>
    </form>
    <button id="locate-btn">Get Current Location</button>
  </section>
</template>

<script>
  export default {
    name: "find-place"
  }
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