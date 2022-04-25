<template>
  <div class="col">
    <div class="card h-100">
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
        <p v-if="project.tech" class="card-text">
          Технологии: <span class="badge bg-info">{{ project.tech }}</span>
        </p>
        <p v-if="project.tags" class="card-text">Теги: {{ project.tags }}</p>
        <p v-if="project.term" class="card-text">Понятия: {{ project.term }}</p>
        <a
          v-if="project.url"
          :href="project.url"
          target="_blank"
          class="card-link stretched-link"
          >Перейти</a
        >
      </div>
      <div class="card-footer">
        <div v-if="project.progress" class="progress">
          <div
            class="progress-bar"
            role="progressbar"
            :style="'width: ' + project.progress"
            :aria-valuenow="project.progress"
            aria-valuemin="0"
            aria-valuemax="100"
          >
            {{ project.progress }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProjectCard",
  props: ["project"],
};
</script>

<style scoped></style>
