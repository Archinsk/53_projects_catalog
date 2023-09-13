<template>
  <div id="admin-view">
    <div class="container">
      <template v-for="(projectDbItem, cardIndex) of projectsDb">
        <ProjectCard
          v-if="projectDbItem.status !== 'Удалён'"
          :project="projectDbItem"
          :is-active-list="isActiveList"
          :card-index="cardIndex"
          :key="projectDbItem.id"
          @flip-large-card="$emit('flip-large-card', $event)"
        />
      </template>
    </div>
  </div>
</template>

<script>
import ProjectCard from "../components/ProjectCard";
// import TheHeader from "../components/TheHeader";

export default {
  name: "Admin",
  components: {
    ProjectCard,
    // TheHeader,
  },
  props: ["projectsDb", "isActiveList"],

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
};
</script>
>

<style lang="scss" scoped></style>
