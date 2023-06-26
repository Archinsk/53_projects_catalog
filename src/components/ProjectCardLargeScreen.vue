<template>
  <vb-card footer image-position="top" :class="cardClass">
    <template v-slot:card-image-top>
      <img
        v-if="project.image"
        :src="project.image"
        class="card-img-top"
        alt="..."
      />
    </template>
    <template v-slot:card-body>
      <div>
        <h5 class="card-title">{{ project.name }}</h5>
        <p class="card-text opacity-75">
          {{ project.description }}
        </p>
      </div>
      <CollapseButton
        :target-id="`collapse${project.id}`"
        tag="a"
        class="btn btn-primary mt-3"
        >Подробнее</CollapseButton
      >
      <Collapse :id="`collapse${project.id}`">
        <div class="mt-3">
          <p v-if="project.tech" class="card-text">
            Технологии:
            <span
              v-for="(tech, index) of projectTechArray"
              :key="index"
              class="badge bg-info me-1"
              >{{ tech }}</span
            >
          </p>
          <p v-if="project.tags" class="card-text">
            Теги: <span class="opacity-75">{{ project.tags }}</span>
          </p>
          <p v-if="project.term" class="card-text">
            Понятия: <span class="opacity-75">{{ project.term }}</span>
          </p>
          <template v-if="project.repository">
            <a
              :href="project.repository"
              style="z-index: 12000"
              class="btn btn-primary mb-3"
              >GitHub</a
            ><br />
          </template>
          <a
            v-if="project.url"
            :href="project.url"
            target="_blank"
            class="card-link btn btn-primary"
            >Смотреть</a
          >
        </div>
      </Collapse>
    </template>
    <template v-slot:card-footer>
      <vb-progress
        v-if="project.progress"
        :progress-value="+project.progress"
        colored
      />
    </template>
  </vb-card>
</template>

<script>
import CollapseButton from "./universal/BS51CollapseButton";
import Collapse from "./universal/BS51Collapse";
import VbProgress from "./universal/BS51Progress";
import VbCard from "./universal/BS51Card";

export default {
  name: "ProjectCardLargeScreen",
  components: { VbCard, VbProgress, Collapse, CollapseButton },
  props: ["project"],
  computed: {
    cardClass: function () {
      let cardClass = "";
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
    projectTechArray: function () {
      if (this.project.tech) {
        return this.project.tech.split(", ");
      } else {
        return [];
      }
    },
  },
};
</script>

<style scoped></style>
