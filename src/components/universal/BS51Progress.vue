<template>
  <div class="progress">
    <div
      class="progress-bar"
      :class="progressClass"
      role="progressbar"
      :style="`width: ${progressValue}%`"
      :aria-valuenow="progressValue"
      aria-valuemin="0"
      aria-valuemax="100"
    >
      {{ progressValue }}%
    </div>
  </div>
</template>

<script>
export default {
  name: "VbProgress",
  props: {
    progressValue: Number,
    colored: Boolean,
  },
  computed: {
    progressClass() {
      let progressClass = "";
      if (this.colored) {
        if (this.progressValue <= 20) {
          progressClass += "progress-20";
        } else if (this.progressValue <= 40) {
          progressClass += "progress-40";
        } else if (this.progressValue <= 60) {
          progressClass += "progress-60";
        } else if (this.progressValue <= 80) {
          progressClass += "progress-80";
        } else {
          progressClass += "progress-100";
        }
      }
      return progressClass;
    },
  },
};
</script>

<style lang="scss" scoped>
.progress {
  background-color: #330d47;
}
.progress-20 {
  /*background-color: #dc3545;*/
  background-color: #ee609c;
}
.progress-40 {
  /*background-color: #ee6420;*/
  background-color: #cd5db5;
}
.progress-60 {
  /*background-color: #ffc107;*/
  background-color: #ad5bce;
}
.progress-80 {
  /*background-color: #52c315;*/
  background-color: #8c58e6;
}
.progress-100 {
  /*background-color: #198754;*/
  background-color: #6b55ff;
}
</style>
