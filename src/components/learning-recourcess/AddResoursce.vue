<template>
    <base-dialog v-if="inputIsInvalid" title="Invalid Input" @close="hideDialog">
<template #default>
    <p>Unfortunately, at least one input value is invalid</p>
    <p>Please check all inputs and make sure that you entered at least few characters into each input field </p>
</template>
<template #actions>
    <base-button @click="hideDialog">Okay</base-button>
</template>
</base-dialog>
    <base-card>
    <form @submit.prevent="addResource">
<div class="form-control">
<label for="title">Title</label>
<input id="title" name="title" type="text" v-model="title">
</div>
<div class="form-control">
<label for="description">Description</label>
<textarea name="description" id="description" rows="3" v-model="description"></textarea>
</div>
<div class="form-control">
<label for="link">Link</label>
<input type="url" name="link" id="link" v-model="link">
</div>
<div>
    <base-button type="submit" @click="">Add Resource</base-button>
</div>
    </form>
    </base-card>
</template>

<script>
export default{
data() {
    return {
        title:'',
        description:'',
        link:'',
        inputIsInvalid: false
    }
},
inject:['resources','setSelectedTab'],
methods:{
    addResource(){
        const resource = {
            id:this.title + Math.random(),
            title: this.title,
            description: this.description,
            link:this.link,
        }

        if (this.title.trim() === '' ||this.description.trim() === ''|| this.link.trim() ==='') {
            this.inputIsInvalid = true
        }
        else{
            this.setSelectedTab('stored-resources')
            this.resources.unshift(resource)
        }        
        console.log(this.selectedTab);
    },
    hideDialog(){
        this.inputIsInvalid = false
    }
}
}
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>