<template>
  <project-card-large-screen :project="project" class="d-none d-lg-block" />
  <project-card-small-screen :project="project" class="d-block d-lg-none" />
</template>

<script>
import ProjectCardLargeScreen from "./ProjectCardLargeScreen";
import ProjectCardSmallScreen from "./ProjectCardSmallScreen";

export default {
  name: "ProjectCard",
  components: {
    ProjectCardSmallScreen,
    ProjectCardLargeScreen,
  },
  props: ["project"],
};
</script>

<style lang="scss" scoped>
#adminView {
  .project-completed {
    background-color: gold;
  }

  .project-private-completed {
    background-color: lightyellow;
  }
}
</style>
