<template>
  <a
    v-if="tag === 'a'"
    class="btn-collapse"
    data-bs-toggle="collapse"
    :href="'#' + targetId"
    role="button"
    aria-expanded="false"
    :aria-controls="targetId"
  >
    <slot></slot>
  </a>
  <button
    v-else
    class="btn btn-collapse"
    type="button"
    data-bs-toggle="collapse"
    :data-bs-target="'#' + targetId"
    aria-expanded="false"
    :aria-controls="targetId"
    @click="$emit('click')"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "CollapseButton",
  props: ["targetId", "tag"],
};
</script>
