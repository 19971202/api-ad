<template>
  <div class="address">
    <input type="text" v-model="text" />
    <button @click="add">住所自動入力</button>
    <p>Address:{{ id }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      text:"",
      id:""
    };
  },
  methods: {
      async add() {
      let item =  await axios.get(
      `https://apis.postcode-jp.com/api/v4/postcodes/${this.text}?apiKey=Bjyqpn5O3i7Cfybt80iSLbO9JLTYYfnA4Y12apL`
       );
      this.id = item.data[0].allAddress;
      console.log(item);
    }
  },
};


</script>