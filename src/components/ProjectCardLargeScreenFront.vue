<template>
  <vb-card image-position="top" :class="cardClass">
    <template v-slot:card-image-top>
      <div class="card-img-top" :style="largeCardImageStyle" />
    </template>
    <template v-slot:card-body>
      <div class="project-description">
        <h5 class="card-title">{{ project.name }}</h5>
        <p class="card-text opacity-75">
          {{ project.description }}
        </p>
      </div>
      <div class="d-flex align-items-center justify-content-between">
        <a
          v-if="project.repository"
          :href="project.repository"
          target="_blank"
          class="btn btn-info btn-round"
          ><svg
            height="24"
            viewBox="0 0 16 16"
            version="1.1"
            width="24"
            fill="white"
          >
            <path
              d="M8 0c4.42 0 8 3.58 8 8a8.013 8.013 0 0 1-5.45 7.59c-.4.08-.55-.17-.55-.38 0-.27.01-1.13.01-2.2 0-.75-.25-1.23-.54-1.48 1.78-.2 3.65-.88 3.65-3.95 0-.88-.31-1.59-.82-2.15.08-.2.36-1.02-.08-2.12 0 0-.67-.22-2.2.82-.64-.18-1.32-.27-2-.27-.68 0-1.36.09-2 .27-1.53-1.03-2.2-.82-2.2-.82-.44 1.1-.16 1.92-.08 2.12-.51.56-.82 1.28-.82 2.15 0 3.06 1.86 3.75 3.64 3.95-.23.2-.44.55-.51 1.07-.46.21-1.61.55-2.33-.66-.15-.24-.6-.83-1.23-.82-.67.01-.27.38.01.53.34.19.73.9.82 1.13.16.45.68 1.31 2.69.94 0 .67.01 1.3.01 1.49 0 .21-.15.45-.55.38A7.995 7.995 0 0 1 0 8c0-4.42 3.58-8 8-8Z"
            ></path></svg
        ></a>
        <button v-else class="btn btn-info btn-round" disabled>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="24"
            viewBox="0 -960 960 960"
            width="24"
            fill="white"
          >
            <path
              d="M240-80q-33 0-56.5-23.5T160-160v-400q0-33 23.5-56.5T240-640h40v-80q0-83 58.5-141.5T480-920q83 0 141.5 58.5T680-720v80h40q33 0 56.5 23.5T800-560v400q0 33-23.5 56.5T720-80H240Zm0-80h480v-400H240v400Zm240-120q33 0 56.5-23.5T560-360q0-33-23.5-56.5T480-440q-33 0-56.5 23.5T400-360q0 33 23.5 56.5T480-280ZM360-640h240v-80q0-50-35-85t-85-35q-50 0-85 35t-35 85v80ZM240-160v-400 400Z"
            />
          </svg>
        </button>
        <a
          v-if="project.url"
          :href="project.url"
          target="_blank"
          class="btn btn-primary rounded-pill"
          >Смотреть</a
        >
        <button v-else class="btn btn-primary rounded-pill" disabled>
          Смотреть
        </button>
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
import VbCard from "./universal/BS51Card";

export default {
  name: "ProjectCardLargeScreenFront",
  components: { VbCard },
  props: ["project"],
  computed: {
    cardClass: function () {
      let cardClass = "card-front-side";
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
    largeCardImageStyle: function () {
      const imageUrl = this.project.image
        ? this.project.image
        : "images/default.jpg";
      return `background: url("${imageUrl}") center center / cover no-repeat;`;
    },
  },
};
</script>
