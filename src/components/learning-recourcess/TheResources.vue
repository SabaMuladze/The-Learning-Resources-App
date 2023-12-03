<template>
    <base-card>
        <base-button @click="setSelectedTab('stored-resources')">Stored Resources</base-button>
        <base-button @click="setSelectedTab('add-resource')">Add Resource</base-button>
    </base-card>
    <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResoursce.vue';
export default{
    data() {
        return {
            selectedTab: 'stored-resources',
            storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentaition',
          link: 'https://vuejs.org/'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to Google',
          link: 'https://google.com/'
        }
      ]
        }
    },
    provide(){
return{
    resources: this.storedResources
}
    },
    methods:{
        setSelectedTab(tab){
            this.selectedTab = tab
        }
    },
    components:{
        StoredResources,
        AddResource
    }
}
</script>

<style></style>