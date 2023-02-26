<template>
  <div id="app">
    <TheHeaderVue title="Learning Resources" ></TheHeaderVue>
    <TheResources></TheResources>
  </div>
</template>

<script>
import TheHeaderVue from './components/Layouts/TheHeader.vue';
import TheResources from './components/Learning-resources/TheLearningResources.vue';
export default {
  components: {
    TheHeaderVue,
    TheResources,
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
