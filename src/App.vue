<template>
  <TheHeader />
  <router-link to="/">Главная</router-link> |
  <router-link to="/registry">Реестр</router-link> |
  <router-link to="/admin">Админка</router-link>
  <!--  <router-link to="/">Главная</router-link>-->
  <!--  <router-link :to="/">Главная</router-link>-->
  <router-view
    :projects-db="projects"
    @flip-large-card="flipLargeCard($event)"
  />
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
    async getProjects() {
      let baseUrl = this.url;
      await axios
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
            project.largeCardFlip = false;
            project.smallCardFlipSide = 1;
          });
          this.projects = JSON.parse(JSON.stringify(projects));
        });
    },

    flipLargeCard(projectId) {
      console.log(projectId);
      let projects = [];
      for (let i = 0; i < this.projects.length; i++) {
        console.log(this.projects[i].id);
        let project = this.projects[i];
        if (project.id === projectId) {
          if (project.largeCardFlip) {
            project.largeCardFlip = false;
          } else {
            project.largeCardFlip = true;
          }
        } else {
          project.largeCardFlip = false;
        }
        projects.push(project);
      }
      console.log(projects);
    },
  },

  mounted: async function () {
    await this.getProjects();
  },
};
</script>
