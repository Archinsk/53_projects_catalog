<template>
  <vb-card :class="cardClass">
    <template v-slot:card-body>
      <div>
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
      </div>
      <div class="text-end">
        <vb-progress
          v-if="project.progress"
          :progress-value="+project.progress"
          colored
          class="mb-3"
        />
        <button
          class="btn btn-info btn-round"
          @click="$emit('flip-large-card', project.id)"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="24"
            viewBox="0 -960 960 960"
            width="24"
            fill="white"
          >
            <path
              d="M478-240q21 0 35.5-14.5T528-290q0-21-14.5-35.5T478-340q-21 0-35.5 14.5T428-290q0 21 14.5 35.5T478-240Zm-36-154h74q0-33 7.5-52t42.5-52q26-26 41-49.5t15-56.5q0-56-41-86t-97-30q-57 0-92.5 30T342-618l66 26q5-18 22.5-39t53.5-21q32 0 48 17.5t16 38.5q0 20-12 37.5T506-526q-44 39-54 59t-10 73Zm38 314q-83 0-156-31.5T197-197q-54-54-85.5-127T80-480q0-83 31.5-156T197-763q54-54 127-85.5T480-880q83 0 156 31.5T763-763q54 54 85.5 127T880-480q0 83-31.5 156T763-197q-54 54-127 85.5T480-80Zm0-80q134 0 227-93t93-227q0-134-93-227t-227-93q-134 0-227 93t-93 227q0 134 93 227t227 93Zm0-320Z"
            />
          </svg>
        </button>
      </div>
    </template>
  </vb-card>
</template>

<script>
import VbProgress from "./universal/BS51Progress";
import VbCard from "./universal/BS51Card";

export default {
  name: "ProjectCardLargeScreenBack",
  components: { VbCard, VbProgress },
  props: ["project"],
  computed: {
    cardClass: function () {
      let cardClass = "card-back-side";
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
