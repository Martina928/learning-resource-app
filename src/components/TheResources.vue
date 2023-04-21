<template>
  <BaseCard>
    <BaseButton @click="selectedTabClick('ResourceList')" :mode="resourceListMode">Resource List</BaseButton>
    <BaseButton @click="selectedTabClick('AddResource')" :mode="addResourceMode">Add Resource</BaseButton>
  </BaseCard>
  <keep-alive>
    <component :is="selectTab"></component>
  </keep-alive>
</template>

<script>
import ResourceList from './ResourceList.vue';
import AddResource from './AddResource.vue'

export default {
  components: {
    ResourceList,
    AddResource
  },
  data() {
    return {
      selectTab: "ResourceList",
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official guide',
          description: 'This is Vue official guide.',
          url: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'You can search anything on Google.',
          url: 'https://google.com'
        }
      ]
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addedResource,
    }
  },
  computed: {
    resourceListMode() {
      return this.selectTab === 'ResourceList' ? null : 'flat';
    },
    addResourceMode() {
      return this.selectTab === 'AddResource' ? null : 'flat';
    }
  },
  methods: {
    selectedTabClick(cmp) {
      this.selectTab = cmp;
    },
    addedResource(addTitle, addDescription, addUrl) {
      const newResource = {
        id: addTitle,
        title: addTitle,
        description: addDescription,
        url: addUrl
      };
      this.storedResources.push(newResource);
    }
  },
}
</script>