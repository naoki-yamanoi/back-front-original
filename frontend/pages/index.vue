<template>
  <div>
    <Tutorial />
    <div>
      <button @click="test">ボタン</button>
      <p>{{ test }}</p>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Axios from 'axios';

export default Vue.extend({
  name: 'IndexPage',
  data() {
    return {
        test: "aaaaaaaa",
      }
  },
  mounted() {
    this.asyncData();
  },
  methods: {
    async asyncData() {
      const response = await Axios.get('http://localhost:8080/api/');
      console.log(response.data);
    }
  }
})
</script>
