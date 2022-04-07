<template>
<div>
  <h1>Annonces</h1>
  <ul id="example-1">
    <li v-for="estate in estates" :key="estate.id">
      <NuxtLink :to="{name:'realestates-id',params:{id:estate.id}}">
      {{ estate.attributes.Title }}
      </NuxtLink>
    </li>
  </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data(){
      return{
            estates:[],
      }
  },
  created: function(){
    axios({
      url:"http://localhost:1337/api/real-estates",
      method:'get',
    }).then((response)=>{
      response.data.data.forEach(estate => {
        this.estates.push(estate)
      });
    })
  }
}
</script>