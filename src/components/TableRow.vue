<template>
  <tr>
    <!--    <th scope="row">{{ row.id }}</th>-->
    <!--    <td>{{ row.num }}</td>-->
    <!--    <td>{{ row.name }}</td>-->
    <!--    <td>Сайт для тестирования и демострации личных проектов</td>-->
    <!--    <td></td>-->
    <!--    <td>-->
    <!--      <a href="https://www.d-skills.ru/index.html" target="_blank"-->
    <!--        >https://www.d-skills.ru/index.html</a-->
    <!--      >-->
    <!--    </td>-->
    <!--    <td>HTML, Bootstrap 4.4.1</td>-->
    <!--    <td>-&#45;&#45;</td>-->
    <!--    <td>-&#45;&#45;</td>-->
    <!--    <td>Демонстрационный</td>-->
    <!--    <td>Надо доделать/переделать</td>-->
    <!--    <td>80%</td>-->
    <!--    <td>Хостинг</td>-->
    <!--    <td>-</td>-->
    <!--    <td>+</td>-->
    <!--    <td>-->
    <!--      «-» - неполный перечень проектов, грубый дизайн, крупные карточки-->
    <!--      мобильной версии-->
    <!--    </td>-->
        <template v-for="(cell, key, index) of row">
    <TableCell
      v-if="cols[index].visibility"
      :key="index"
      :index="index"
      :cell="cell"
      :type="cols[index].type"
    />
        </template>
  </tr>
</template>

<script>
import TableCell from "./TableCell";

export default {
  name: "TableRow",
  components: {
    TableCell,
  },
  props: ["row", "cols"],
};
</script>

<style scoped></style>
