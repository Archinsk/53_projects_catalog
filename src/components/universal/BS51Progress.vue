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
.progress-20 {
  background-color: #dc3545;
}
.progress-40 {
  background-color: #ee6420;
}
.progress-60 {
  background-color: #ffc107;
}
.progress-80 {
  background-color: #52c315;
}
.progress-100 {
  background-color: #198754;
}
</style>
