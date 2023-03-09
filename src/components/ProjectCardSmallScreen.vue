<template>
  <div class="col-12">
    <vb-card image-position="top" :class="cardClass" horizontal>
      <template v-slot:card-image-top>
        <img
          v-if="project.image"
          :src="project.image"
          class="img-fluid rounded-start"
          alt="..."
        />
      </template>
      <template v-slot:card-body>
        <div class="d-flex flex-column justify-content-between">
          <div>
            <h5 class="card-title">{{ project.name }}</h5>
            <p class="card-text">
              {{ project.description }}
            </p>
          </div>
          <CollapseButton :target-id="`collapse${project.id}`" tag="a"
            >Подробнее</CollapseButton
          >
        </div>
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
      </template>
    </vb-card>
  </div>
</template>

<script>
import CollapseButton from "./universal/BS51CollapseButton";
import Collapse from "./universal/BS51Collapse";
import VbCard from "./universal/BS51Card";

export default {
  name: "ProjectCardSmallScreen",
  components: { VbCard, Collapse, CollapseButton },
  props: ["project"],
  computed: {
    cardClass: function () {
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
    },
  },
};
</script>

<style scoped></style>
