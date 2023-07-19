<template>
  <div class="small-card-face small-card-third-face">
    <div>{{ project.tech }}</div>
    <div>{{ project.tags }}</div>
  </div>
</template>

<script>
export default {
  name: "ProjectCardSmallScreenThirdFace",
  props: ["project"],
};
</script>
