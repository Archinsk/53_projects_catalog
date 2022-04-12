<template>
  <TheHeader />
  <router-view />
</template>

<script>
import TheHeader from "./components/TheHeader";

export default {
  name: "App",
  components: {
    TheHeader,
  },
};
</script>
