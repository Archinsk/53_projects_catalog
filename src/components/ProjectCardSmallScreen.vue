<template>
  <div>
    <div class="project-small-card" :style="rotateStyle">
      <project-card-small-screen-first-face
        :project="project"
        @click="step++"
      />
      <project-card-small-screen-second-face
        :project="project"
        @click="step++"
      />
      <project-card-small-screen-third-face
        :project="project"
        @click="step++"
      />
      <project-card-small-screen-fourth-face
        :project="project"
        @click="step++"
      />
    </div>
  </div>
</template>

<script>
// import CollapseButton from "./universal/BS51CollapseButton";
// import Collapse from "./universal/BS51Collapse";
// import VbCard from "./universal/BS51Card";

import ProjectCardSmallScreenFirstFace from "./ProjectCardSmallScreenFirstFace";
import ProjectCardSmallScreenSecondFace from "./ProjectCardSmallScreenSecondFace";
import ProjectCardSmallScreenThirdFace from "./ProjectCardSmallScreenThirdFace";
import ProjectCardSmallScreenFourthFace from "./ProjectCardSmallScreenFourthFace";
export default {
  name: "ProjectCardSmallScreen",
  components: {
    ProjectCardSmallScreenFourthFace,
    ProjectCardSmallScreenThirdFace,
    ProjectCardSmallScreenSecondFace,
    ProjectCardSmallScreenFirstFace,
  },
  // components: { VbCard, Collapse, CollapseButton },
  props: ["project", "cardIndex"],
  data() {
    return {
      step: -1,
    };
  },
  computed: {
    /*cardClass: function () {
      let cardClass = "card";
      if (
        +this.project.progress === 100 &&
        this.project.purpose === "Демонстрационный"
      ) {
        cardClass += " project-completed";
      } else if (this.project.progress === "100%") {
        cardClass += " project-private-completed";
      }
      return cardClass;
    },*/
    rotateStyle() {
      return `transform: rotate3d(1, 0, 0, ${90 * this.step}deg);`;
    },
    loadingRotateDelay() {
      return 1800 + this.cardIndex * 100;
    },
  },

  mounted() {
    setTimeout(() => {
      this.step++;
    }, this.loadingRotateDelay);
  },
};
</script>

<style scoped></style>
