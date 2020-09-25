<template>
  <section id="share-controls">
    <input
      id="share-link"
      type="text"
      readonly
      v-model="sharableLink"
    />
    <button id="share-btn" :disabled="disabled">Share Place</button>
  </section>
</template>

<script>
export default {
  name: "share-place",
  created() {
    /* eslint-disable no-undef */
    eventBus.$on("gotAddressAndCoords", data => this.createSharableLink(data));
  },
  data () {
    return {
      sharableLink: "Select a place to get a sharable link.",
      disabled: true
    }
  },
  methods: {
    createSharableLink (data) {
      const long = +data.coordinates.long.toFixed(2);
      const lat = +data.coordinates.lat.toFixed(2);
      this.disabled = false;
      this.sharableLink = `${location.origin}/my-place?address=${encodeURI(data.address)}&lat=${lat}&long=${long}`;
    }
  }
};
</script>

<style lang="scss">
#share-controls {
  width: 40rem;
  max-width: 90%;
  margin: 2rem auto;
  border: 1px solid #ccc;
  padding: 1rem;
  text-align: center;

  input {
    font-size: 1.15rem;
  }
}

label,
input {
  display: block;
  width: 100%;
}

label {
  font-weight: bold;
  margin: 0.5rem 0;
}

input {
  font: inherit;
  padding: 0.15rem 0.25rem;
  border: 1px solid #ccc;
  font-size: 3rem;
  text-align: center;
  color: #696969;
  &:focus {
    outline: none;
    background: #efe3ff;
    border-color: #36007c;
  }
}

button {
  font: inherit;
  font-size: 1.25rem;
  background: #36007c;
  color: white;
  border: 1px solid #36007c;
  border-radius: 6px;
  padding: 0.5rem 1.5rem;
  margin: 0.5rem 0;
  cursor: pointer;

  &:focus {
    outline: none;
  }
  &:hover,
  &:active {
    background: #55007c;
    border-color: #55007c;
  }

  &:disabled,
  &:disabled:hover,
  &:disabled:active {
    background: #ccc;
    color: #9b9b9b;
    border-color: #ccc;
    cursor: not-allowed;
  }
}
</style>
