<template>
  <div class="home">
    <table class="table table-sm">
      <thead>
        <tr>
          <th scope="col">id</th>
          <th scope="col">#</th>
          <th scope="col">Наименование</th>
          <th scope="col">Описание</th>
          <th scope="col">Каталог</th>
          <th scope="col">Ссылка</th>
          <th scope="col">Изображение</th>
          <th scope="col">Технологии</th>
          <th scope="col">Теги</th>
          <th scope="col">Понятия</th>
          <th scope="col">Назначение</th>
          <th scope="col">Статус</th>
          <th scope="col">Завершенность</th>
          <th scope="col">Исходник</th>
          <th scope="col">GitHub</th>
          <th scope="col">Хостинг</th>
          <th scope="col">Комментарии</th>
        </tr>
      </thead>
      <tbody v-if="projects.length > 0">
        <TableRow
          v-for="projectItem of projects"
          :key="projectItem.id"
          :row="projectItem"
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
      url: "https://www.d-skills.ru/53_projects_catalog/",
      projects: [],
    };
  },

  methods: {
    getProjects() {
      axios.post(this.url + "php/getprojects.php", {}).then((response) => {
        console.log(response);
        this.projects = response.data;
      });
    },
  },

  mounted() {
    this.getProjects();
  },
};
</script>
>
