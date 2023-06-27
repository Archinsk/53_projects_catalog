<template>
  <div id="homeView">
    <div class="container">
      <!--<div
        class="row row-cols-1 row-cols-lg-3 row-cols-xl-4 row-cols-xxl-5 g-3"
      >
        <template v-for="projectDbItem of projectsDb">
          <ProjectCard
            v-if="
              projectDbItem.purpose === 'Демонстрационный' &&
              projectDbItem.status !== 'Удалён' &&
              projectDbItem.progress >= 70
            "
            :project="projectDbItem"
            :key="projectDbItem.id"
          />
        </template>
      </div>-->
      <div class="new-grid">
        <template v-for="projectDbItem of filtredProjects">
          <ProjectCard
            v-if="
              projectDbItem.purpose === 'Демонстрационный' &&
              projectDbItem.status !== 'Удалён' &&
              projectDbItem.progress >= 70
            "
            :project="projectDbItem"
            :key="projectDbItem.id"
            @flip-large-card="$emit('flip-large-card', $event)"
          />
        </template>
      </div>
    </div>
  </div>
</template>

<script>
import ProjectCard from "../components/ProjectCard";
// import TheHeader from "../components/TheHeader";

export default {
  name: "Home",
  components: {
    ProjectCard,
    // TheHeader,
  },
  props: ["projectsDb"],

  data() {
    return {
      columns: [
        {
          name: "id",
          type: "number",
          visibility: false,
        },
        {
          name: "#",
          type: "string",
          visibility: true,
        },
        {
          name: "Наименование",
          type: "string",
          visibility: true,
        },
        {
          name: "Описание",
          type: "string",
          visibility: true,
        },
        {
          name: "Каталог",
          type: "string",
          visibility: false,
        },
        {
          name: "Ссылка",
          type: "link",
          visibility: true,
        },
        {
          name: "Изображение",
          type: "image",
          visibility: false,
        },
        {
          name: "Технологии",
          type: "string",
          visibility: false,
        },
        {
          name: "Теги",
          type: "string",
          visibility: false,
        },
        {
          name: "Понятия",
          type: "string",
          visibility: false,
        },
        {
          name: "Назначение",
          type: "string",
          visibility: false,
        },
        {
          name: "Статус",
          type: "string",
          visibility: false,
        },
        {
          name: "Завершенность",
          type: "string",
          visibility: false,
        },
        {
          name: "Исходник",
          type: "string",
          visibility: true,
        },
        {
          name: "GitHub",
          type: "boolean",
          visibility: true,
        },
        {
          name: "Хостинг",
          type: "boolean",
          visibility: true,
        },
        {
          name: "Комментарии",
          type: "string",
          visibility: false,
        },
      ],
    };
  },

  computed: {
    filtredProjects() {
      let filtredProjects = this.projectsDb.filter((project) => {
        return (
          project.purpose === "Демонстрационный" &&
          project.status !== "Удалён" &&
          project.progress >= 70
        );
      });
      return filtredProjects;
    },
  },
};
</script>
>
