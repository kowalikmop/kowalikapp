<template>

 <div class="container">
  <div class="row">
    <div class="col-sm">
  <input v-model="apperTitle"/>
    </div>
    <div class="col-sm">
 <button @click="textinput">Pobierz</button>
    </div>
    </div>
      <div class="row">
    <div class="col-sm">
     <ul>
       <li v-for="item in wynikzapi" :key="item.data[0].nasa_id">
         <h3>{{item.data[0].title}}</h3>
         <img :src="`${item.links[0].href}`" alt="">
       </li>
     </ul>
    </div>
  </div>
</div>
</template>
<script>
import axios from 'axios';

export default {
  data() {
    return {
      apperTitle: '',
      wynikzapi: [],
    };
  },
  methods: {
    textinput() {
      axios.get(`https://images-api.nasa.gov/search?q=${this.apperTitle}&media_type=image`).then((response) => {
        console.log(this.apperTitle);
        this.wynikzapi = response.data.collection.items;
      });
    },
  },
};
</script>
