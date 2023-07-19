<template>
  <div class="small-card-face small-card-second-face">
    {{ project.description }}
  </div>
</template>

<script>
export default {
  name: "ProjectCardSmallScreenSecondFace",
  props: ["project"],
};
</script>
