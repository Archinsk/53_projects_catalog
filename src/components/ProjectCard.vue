<template>
  <div class="col">
    <div :class="cardClass">
      <img
        v-if="project.image"
        :src="project.image"
        class="card-img-top"
        alt="..."
      />
      <div class="card-body">
        <h5 class="card-title">{{ project.name }}</h5>
        <p class="card-text">
          {{ project.description }}
        </p>
        <CollapseButton :target-id="`collapse${project.id}`"
          >Подробнее</CollapseButton
        >
        <Collapse :id="`collapse${project.id}`">
          <p v-if="project.tech" class="card-text">
            Технологии: <span class="badge bg-info">{{ project.tech }}</span>
          </p>
          <p v-if="project.tags" class="card-text">Теги: {{ project.tags }}</p>
          <p v-if="project.term" class="card-text">
            Понятия: {{ project.term }}
          </p>
          <!--        stretched-link-->
          <a
            v-if="project.url"
            :href="project.url"
            target="_blank"
            class="card-link"
            >Перейти</a
          >
          <template v-if="project.repository">
            <br />
            <a :href="project.repository" style="z-index: 12000">GitHub</a>
          </template>
        </Collapse>
      </div>
      <div class="card-footer">
        <div v-if="project.progress" class="progress">
          <div
            class="progress-bar"
            role="progressbar"
            :style="`width: ${project.progress}%`"
            :aria-valuenow="project.progress"
            aria-valuemin="0"
            aria-valuemax="100"
          >
            {{ project.progress }}%
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CollapseButton from "./universal/BS51CollapseButton";
import Collapse from "./universal/BS51Collapse";
export default {
  name: "ProjectCard",
  components: { Collapse, CollapseButton },
  props: ["project"],
  computed: {
    cardClass: function () {
      let cardClass = "card h-100";
      if (
        +this.project.progress === 100 &&
        this.project.purpose === "Демонстрационный"
      ) {
        cardClass += " project-completed";
      } else if (this.project.progress === "100%") {
        cardClass += " project-private-completed";
      }
      return cardClass;
    },
  },
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
