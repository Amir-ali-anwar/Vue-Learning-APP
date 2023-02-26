<template>
  <base-card>
    <base-button
      :mode="storedResButtonMode"
      @click="settoggleTab('store-resources')"
      >Stored Resources</base-button
    >
    <base-button :mode="addResButtonMode" @click="settoggleTab('add-resource')"
      >Add Resources</base-button
    >
  </base-card>
  <component :is="selectedTab"></component>
</template>
  <script>
import StoreResources from './StoreResources.vue';
import AddResource from './AddLearningResource.vue';
export default {
  components: {
    StoreResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: 'stored-resources',
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
  provide() {
    return {
      resources: this.storedResources,
      addResources:this.addResources
    };
  },
  methods: {
    settoggleTab(tab) {
      this.selectedTab = tab;
    },
    addResources(title,description,link){
      const newresource={
        id: new Date().toISOString(),
        title,description,link
      }
      this.storedResources.unshift(newresource);
      this.selectedTab = 'stored-resources';
    }
  },
  computed:{
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  }
};
</script>