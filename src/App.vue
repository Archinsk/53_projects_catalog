<template>
  <TheHeader />
  <router-link to="/">Главная</router-link> |
  <router-link to="/registry">Реестр</router-link> |
  <router-link to="/admin">Админка</router-link>
  <!--  <router-link to="/">Главная</router-link>-->
  <!--  <router-link :to="/">Главная</router-link>-->
  <router-view :projects-db="projects" />
</template>

<script>
import TheHeader from "./components/TheHeader";
import axios from "axios";

export default {
  name: "App",
  components: {
    TheHeader,
  },

  data() {
    return {
      url: "https://www.d-skills.ru/",
      projects: [],
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
            if (project.image) {
              project.image = baseUrl + project.image;
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
