<template>
    <ul>
    <learning-resource v-for="resource in resources" :key="resource.id" :link="resource.link"
      :title="resource.title" :description="resource.description" :id="resource.id"></learning-resource>
  </ul>
</template>

<script>
import LearningResource from './LearningResource.vue';
export default{
    data() {
        return {
            
        }
    },
    inject:['resources'],
    components:{
        LearningResource
    }
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>