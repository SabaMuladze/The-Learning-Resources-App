<template>
    <base-card>
        <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButton">Stored Resources</base-button>
        <base-button @click="setSelectedTab('add-resource')" :mode="addResButton">Add Resource</base-button>
    </base-card>
    <keep-alive>
        <component :is="selectedTab"></component>
    </keep-alive>
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
    resources: this.storedResources,
    deleteRes: this.deleteResource,
    setSelectedTab: this.setSelectedTab
}
    },
    methods:{
        setSelectedTab(tab){
            this.selectedTab = tab
        },
        deleteResource(resId){
         const resIndex = this.storedResources.findIndex(res => res.id === resId)
         this.storedResources.splice(resIndex,1)
        }
    },
    components:{
        StoredResources,
        AddResource
    },
    computed:{
        storedResButton(){
            return this.selectedTab === 'stored-resources' ? null : 'flat'
        },
        addResButton(){
            return this.selectedTab === 'add-resource' ? null : 'flat'
        }
    }
}
</script>

<style></style>