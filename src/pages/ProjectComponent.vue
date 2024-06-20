<template>
    <div v-if="project">
        <h1>{{ project.title }}</h1>
        <img :src="store.imgBasePath + project.image" :alt="project.title">
        <p>{{ project.content }}</p>
        <span>{{ project.category?.name }}</span>
        <RouterLink :to="{ name: 'single-project', params: { 'slug': 'boolzapp' } }">Leggi
            altro articolo</RouterLink>
    </div>
</template>

<script>
import { store } from '../store';
import axios from 'axios';

export default {
    name: 'ProjectComponent',
    data() {
        return {
            store,
            project: null
        }
    },
    methods: {
        getProject() {
            console.log(this.$route);
            axios.get(`${this.store.apiBaseUrl}/projects/${this.$route.params.slug}`).then((res) => {
                console.log(res.data.results);
                this.project = res.data.results;
            }).catch((error) => {
                this.$router.push({ name: 'not-found' });
            }).finally();
        }
    },
    mounted() {
        this.getProject();
    },
    created() {
        this.$watch(
            () => this.$route.params,
            (toParams, previousParams) => {
                // react to route changes...
                this.getProject();
            }
        )

    }
}
</script>

<style lang="scss" scoped></style>