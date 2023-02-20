<template>
    <h1> the results are here</h1>
    <div v-for="imag in user" :key="imag.id">
    <img :src="imag.urls.regular">
  </div>
  <div>
    {{displayData()}}
  </div>

</template>

<script>

export default{
    name: 'ResultT',
    data(){
        return {
            word: '',
            user: {}
        }
    },
    methods: {
        displayData(){
            this.user = JSON.parse(localStorage.getItem('user-info')).results;
            
            console.log("awe");
            console.warn(this.user);
        }
    }

 
}

</script>

<style scoped>
img {
    width: 300px;
}
</style>

