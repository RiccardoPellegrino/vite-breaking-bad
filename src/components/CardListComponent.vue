<template>
    <section class="container card-container">
        <div class="container mt-4 mb-2">
            <div v-html="`Found ${characterList.length} characters`" class="found fw-bold"></div>
        </div>
        <CardComponent :characters="characterList" :loading="loading" />
    </section>
</template>

<script>
import axios from 'axios'
import CardComponent from './CardComponent.vue'
export default {
    components: { CardComponent },
    name: 'CardListComponent',
    data() {

        return {
            apiURL: 'https://www.breakingbadapi.com/api/characters',
            characterList: [],
            loading: false
            // cinque: [],
        }
    },
    methods: {
        //chiamata per api come metodo
        getCharacters() {
            this.loading = true;
            axios.get(this.apiURL).then(
                (res) => {
                    console.log(res.data)
                    this.characterList = [...res.data]
                    console.log(this.characterList)
                    this.loading = false;
                },//success

            )
                .catch((error) => {
                    // handle error
                    console.log(error);
                })
        },
        // soloPrimiCinque() {
        //   for (let i = 0; i < 5; i++) {
        //     this.cinque.push(this.characterList[i]);
        //   }
        // }
    },
    created() {
        //chiamata api ad inizio app
        this.getCharacters()
    }
}

</script>

<style lang="scss" scoped>

</style>