<template>
  <div
    class="project-large-card-container"
    :class="project.largeCardFlip ? 'project-large-card-flipped' : ''"
  >
    <project-card-large-screen-front
      :project="project"
      class="d-none d-sm-inline-block"
      @flip-large-card="$emit('flip-large-card', $event)"
    />
    <project-card-large-screen-back
      :project="project"
      class="d-none d-sm-inline-block"
      @flip-large-card="$emit('flip-large-card', $event)"
    />
  </div>
  <project-card-small-screen :project="project" class="d-block d-sm-none" />
</template>

<script>
import ProjectCardSmallScreen from "./ProjectCardSmallScreen";
import ProjectCardLargeScreenFront from "./ProjectCardLargeScreenFront";
import ProjectCardLargeScreenBack from "./ProjectCardLargeScreenBack";

export default {
  name: "ProjectCard",
  components: {
    ProjectCardLargeScreenBack,
    ProjectCardLargeScreenFront,
    ProjectCardSmallScreen,
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
