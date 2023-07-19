<template>
  <div class="small-card-face small-card-first-face">
    {{ project.name }}
  </div>
</template>

<script>
export default {
  name: "ProjectCardSmallScreenFirstFace",
  props: ["project"],
};
</script>
