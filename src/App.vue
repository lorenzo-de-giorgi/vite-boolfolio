<template>
  <div>
    <h1>ciao</h1>
    <ul>
      <li v-for="post in posts" :key="projects.id">{{ projects.title }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import { store } from './store';
  export default {
    name: 'App',
    data() {
      return {
        store,
        projects: []
      }
    },
    methods: {
      getAllProjects() {
        axios.get(this.store.apiBaseURL+'/projects').then((res)=>{
          console.log(res.data);
          this.projects = res.data.results;
        });
      }
    },
    mounted(){
      this.getAllProjects();
    }
  }
</script>

<style lang="scss" scoped>

</style>