<template>
  <div id="home-view">
    <div class="container">
      <ProjectCard
        v-for="projectDbItem of projectsForPublication"
        :project="projectDbItem"
        :key="projectDbItem.id"
        @flip-large-card="$emit('flip-large-card', $event)"
      />
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
    projectsForPublication() {
      let projectsForPublication = this.projectsDb.filter((project) => {
        return (
          project.purpose === "Демонстрационный" &&
          project.status !== "Удалён" &&
          project.progress >= 70
        );
      });
      return projectsForPublication;
    },
  },
};
</script>
>
