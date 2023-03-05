<template>
  <tr :class="rowClass">
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
  computed: {
    rowClass: function () {
      let rowClass = "";
      if (this.row.progress === "100%") {
        rowClass += "project-completed-row";
      }
      return rowClass;
    },
  },
};
</script>

<style scoped></style>
