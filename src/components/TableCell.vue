<template>
  <td v-if="type === 'boolean'">
    <input class="form-check-input" type="checkbox" :checked="+cell" disabled />
  </td>
  <td v-else-if="type === 'link' && cell">
    <a :href="cell" target="_blank">Ссылка</a>
  </td>
  <td v-else>{{ cell }}</td>
</template>

<script>
export default {
  name: "TableCell",
  props: ["cell", "type"],
};
</script>

<style scoped></style>
