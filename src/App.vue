<template>
  <div id="app">
    <TheHeaderVue title="Learning Resources" ></TheHeaderVue>
    <StoredResources :resources="storedResources"></StoredResources>
  </div>
</template>

<script>
import TheHeaderVue from './components/Layouts/TheHeader.vue';
import StoredResources from './components/StoreResources.vue'

export default {
  components: {
    StoredResources,
    TheHeaderVue
  },
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation.',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.com',
        },
      ],
    };
  },
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
