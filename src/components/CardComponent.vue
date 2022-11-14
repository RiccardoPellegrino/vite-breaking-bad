<template>
    <div class="container">
        <div class="row">
            <div class="col" v-for="(item, index) in characters" :key="item.char_id" v-if="!index <= 5">
                <img :src="item.img" :alt="item.name">
                <h3>{{ item.name }}</h3>
                <h5>{{ item.category }}</h5>
                <p>{{ item.status }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardComponent',
    props: ['characters']
}
</script>

<style lang="scss" scoped>

</style>