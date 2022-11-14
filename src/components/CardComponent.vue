<template>
    <div class="container">
        <div v-if="loading" class="d-flex justify-content-center fw-bold display-4 mt-4">
            Sto caricando i dati
        </div>
        <div class="row justify-content-center contenitore" v-if="!loading">
            <div class="bg-secondary">Found 62 characters</div>
            <div class="col col-2 m-3" v-for="(item, index) in characters" :key="item.char_id">
                <div class="character p-3 text-center">
                    <img :src="item.img" :alt="item.name">
                    <h5 class="text-white mt-3">{{ item.name }}</h5>
                    <span class="text-secondary mt-3"> {{ item.category }}</span>
                    <p class="text-secondary mt-2">{{ item.status }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardComponent',
    props: ['characters', 'loading']
}
</script>

<style lang="scss" scoped>
.contenitore {
    background-color: white;
}
</style>