<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>{{ message }}</p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';


export default Vue.extend({
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return {
      message: '',
    };
  },
  async created() {
    console.log(process.env);
    fetch('/api/getMessage?name=Vue.js')
      .then(responce => responce.json() )
      .then(responce => {
        this.message = responce.message;
      }).catch(()=>{
        this.message = 'failed';
      });
  },
});
</script>
