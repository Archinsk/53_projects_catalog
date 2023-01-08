<template>
  <div class="home">
    <table class="table table-sm">
      <thead>
        <tr>
          <!--          <th scope="col">id</th>-->
          <th scope="col">#</th>
          <th scope="col">Наименование</th>
          <th scope="col">Описание</th>
          <!--                    <th scope="col">Каталог</th>-->
          <th scope="col">Ссылка</th>
          <!--                    <th scope="col">Изображение</th>-->
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
      <tbody v-if="projectsDb.length > 0">
        <TableRow
          v-for="projectItem of projectsDb"
          :key="projectItem.id"
          :row="projectItem"
          :cols="columns"
        />
      </tbody>
    </table>
  </div>
</template>

<script>
import TableRow from "../components/TableRow";
// import TheHeader from "../components/TheHeader";

export default {
  name: "Registry",
  components: {
    // TheHeader,
    TableRow,
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
          visibility: true,
        },
        {
          name: "Теги",
          type: "string",
          visibility: true,
        },
        {
          name: "Понятия",
          type: "string",
          visibility: true,
        },
        {
          name: "Назначение",
          type: "string",
          visibility: true,
        },
        {
          name: "Статус",
          type: "string",
          visibility: true,
        },
        {
          name: "Завершенность",
          type: "string",
          visibility: true,
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
          visibility: true,
        },
      ],
    };
  },

  methods: {},

  mounted() {},
};
</script>
>
