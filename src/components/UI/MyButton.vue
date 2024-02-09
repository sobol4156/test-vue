<template>

    <button>
      <slot></slot>
    </button>

</template>

<script>
export default {
    name: 'my-button'
};
</script>

<style scoped>
button {
  block-size: 20px;
  width: 80px;
  background-color: #4caf50; /* Green */
  border: none;
  color: white;
  border-radius: 5px;
  cursor: pointer;
  transition: all linear 0.3s;
}
button:hover {
  background: #3e8641;
  transform: rotate(-5deg);
}
</style>