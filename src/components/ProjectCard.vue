<template>
  <!--  class="project-large-card-container d-none d-sm-inline-block"-->
  <div
    class="project-large-card-container d-sm-inline-block"
    :class="project.largeCardFlip ? 'project-large-card-flipped' : ''"
  >
    <project-card-large-screen-front
      :project="project"
      class="d-sm-inline-block"
      @flip-large-card="$emit('flip-large-card', $event)"
    />
    <project-card-large-screen-back
      :project="project"
      class="d-sm-inline-block"
      @flip-large-card="$emit('flip-large-card', $event)"
    />
  </div>
  <project-card-small-screen
    v-if="false"
    class="project-small-card-container d-block d-sm-none"
    :class="{ show: isActiveList }"
    :project="project"
    :card-index="cardIndex"
    :style="`transition-delay: ${cardIndex * 0.1}s`"
  />
</template>

<script>
import ProjectCardLargeScreenFront from "./ProjectCardLargeScreenFront";
import ProjectCardLargeScreenBack from "./ProjectCardLargeScreenBack";
import ProjectCardSmallScreen from "./ProjectCardSmallScreen";

export default {
  name: "ProjectCard",
  components: {
    ProjectCardSmallScreen,
    ProjectCardLargeScreenBack,
    ProjectCardLargeScreenFront,
  },
  props: ["project", "isActiveList", "cardIndex"],
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
