<template>
  <section id="share-controls">
    <input
      id="share-link"
      type="text"
      readonly
      value="Select a place to get a sharable link."
    />
    <button id="share-btn" disabled>Share Place</button>
  </section>
</template>

<script>
export default {
  name: "share-place"
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
