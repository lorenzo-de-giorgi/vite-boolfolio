<template>
    <div class="card mb-3">
        <div class="row g-0">
            <div class="col-md-4">
                <img :src="getImage" class="img-fluid rounded-start" :alt="item.title">
            </div>
            <div class="col-md-8">
                <div class="card-body">
                    <h5 class="card-title">{{ item.title }}</h5>
                    <p class="card-text" v-html="item.content"></p>
                    <p class="card-text"><small class="text-body-secondary">Last updated: 3 {{ item.updated_at
                            }}</small>
                    </p>
                    <span class="badge rounded-pill text-bg-primary me-3">{{ item.category?.name }}</span>
                    <div class="d-flex justify-content-end">
                        <RouterLink :to="{ name: 'single-project', params: { 'slug': item.slug } }" class="btn btn-success">Leggi articolo</RouterLink>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { store } from '../store';
export default {
    name: 'CardComponent',
    props: ['item'],
    data() {
        return {
            store
        }
    },
    computed: {
        getImage() {

            return this.item.image ? this.store.imgBasePath + this.item.image : '';
        }
    }
}
</script>

<style lang="scss" scoped></style>