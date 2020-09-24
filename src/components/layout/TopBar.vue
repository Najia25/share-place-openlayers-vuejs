<template>
  <div>
    <header>
      <h1><slot></slot></h1>
    </header>
  </div>
</template>

<script>
export default {
  name: "top-bar"
};
</script>

<style lang="scss" scoped>
header {
  background: #36007c;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.26);
  padding: 10px;

  h1 {
    font-size: 1.5rem;
    color: white;
    margin: 0;
  }
}
</style>
