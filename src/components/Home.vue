<template>
    <div class="container">
        
        <div>
            <h1>FotoFinder</h1>
            <input type="text" v-model="keyword" placeholder="Enter keyword" />
            <button v-on:click="searchWord">Search</button>
        </div>
    </div>


    
</template>

<script>
import axios from 'axios'

export default {
  name: 'Home-page',
  data(){       
    return {
      keyword: '',
      /*photo: {},
      photoUrl: ''*/
    }
  },
  methods: {
    async searchWord(){
        console.log("Workinggg");
        console.log(this.keyword);
        let api_key = "Your-Access-key";
        let endpoint = `https://api.unsplash.com/search/photos?query=${this.keyword}&client_id=${api_key}`;

        let result = await axios.get(endpoint);
        //console.warn(result);

        localStorage.setItem("user-info", JSON.stringify(result.data));
        //localStorage.storedData = result.results;

        /*if(result.status == 200 && result.data.length > 0){
            console.log("data is here")
            localStorage.setItem("user-info", JSON.stringify(result.data[0]));
        }*/

        this.$router.push({name: 'Results'});
    }
  }
 /* methods: {
        searchWord(){
        console.log(this.keyword);
        let api_key = "JD53Sd4CGnH8kosQsnaT4dRJl_WqQdHKh0gjnISfaIA";
        let endpoint = `https://api.unsplash.com/search/photos?query=${this.keyword}&client_id=${api_key}`

        fetch(endpoint)
        .then(function (response){
            return response.json();
        })
        .then(this.setReults);
        },
        setReults(jsonData){
        this.photo = jsonData.results;
        console.log(this.photo)
        }
    }*/
}
</script>

<style scoped>
img{
  width: 300px;
  margin: auto;
  margin-bottom: 20px;
}

input{
  width: 400px;
  padding: 20px 30px;
  background-color: #fff;
  border: none;
  margin-right: 10px;  
  margin-top: 10px;
}

h1 {
    font-size: 50px;
    color: #003b32;
    text-align: left;
}

button{
  padding: 20px 30px;
  background-color: #40817a;
  border: none;
  color: #fff;
  cursor: pointer;
}

.container {
    margin: auto;
    height: 100vh;
    background-image: url("../assets/annie-spratt-OTy0mkqc2Yk-unsplash.jpg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}

.container div {
    max-width: 600px;
    position: relative;
    top: 150px;
    margin: auto;
}


</style>
