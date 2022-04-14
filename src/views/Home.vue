<template>
  <div class="home">
    <table class="table table-sm">
      <thead>
        <tr>
          <!--          <th scope="col">id</th>-->
          <th scope="col">#</th>
          <th scope="col">Наименование</th>
          <th scope="col">Описание</th>
          <!--          <th scope="col">Каталог</th>-->
          <th scope="col">Ссылка</th>
          <!--          <th scope="col">Изображение</th>-->
          <!--          <th scope="col">Технологии</th>-->
          <!--          <th scope="col">Теги</th>-->
          <!--          <th scope="col">Понятия</th>-->
          <!--          <th scope="col">Назначение</th>-->
          <!--          <th scope="col">Статус</th>-->
          <!--          <th scope="col">Завершенность</th>-->
          <th scope="col">Исходник</th>
          <th scope="col">GitHub</th>
          <th scope="col">Хостинг</th>
          <!--          <th scope="col">Комментарии</th>-->
        </tr>
      </thead>
      <tbody v-if="projects.length > 0">
        <TableRow
          v-for="projectItem of projects"
          :key="projectItem.id"
          :row="projectItem"
          :cols="columns"
        />
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";
import TableRow from "../components/TableRow";
// import TheHeader from "../components/TheHeader";

export default {
  name: "Home",
  components: {
    // TheHeader,
    TableRow,
  },

  data() {
    return {
      url: "https://www.d-skills.ru/",
      projects: [],
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

  methods: {
    getProjects() {
      let baseUrl = this.url;
      axios
        .post(this.url + "53_projects_catalog/php/getprojects.php", {})
        .then((response) => {
          let projects = response.data;
          projects.forEach(function (project) {
            if (project.url) {
              let newUrl = baseUrl;
              if (project.path) {
                newUrl += project.path + "/";
              }
              newUrl += project.url;
              project.url = newUrl;
            }
          });
          this.projects = projects;
        });
    },
  },

  mounted() {
    this.getProjects();
  },
};
</script>
>
