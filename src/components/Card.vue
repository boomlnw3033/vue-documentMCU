<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <li>
    <slot name="card-header"></slot>
    <slot name="card-button"></slot>
    <slot name="card-content"></slot>
  </li>
</template>

<script>
export default {};
</script>

<style scoped>
li {
  margin: 1rem 0;
  font-size: normal;
  font-weight: normal;
  background: #a9e1eb;
  padding: 0.5rem;
  color: #1f1f1f;
  border-radius: 20px;
}
</style>
