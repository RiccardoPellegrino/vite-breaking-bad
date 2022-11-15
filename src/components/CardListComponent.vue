<template>
    <SearchBarComponent @filterChar="getCharacters" />
    <section class="container card-container bg-white">
        <div class="pt-3">
            <div class="container mt-2 mb-2">
                <div v-html="`Found ${characterList.length} characters`"
                    class="foundCharacter fw-bold bg-dark text-white ">
                </div>
            </div>
        </div>
        <CardComponent :characters="characterList" :loading="loading" />
    </section>
</template>

<script>
import axios from 'axios'
import CardComponent from './CardComponent.vue'
import SearchBarComponent from './SearchBarComponent.vue'
export default {
    components: {
        CardComponent,
        SearchBarComponent
    },
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
        getCharacters(category) {

            let option = null;
            if (category) {
                option = {
                    params: {
                        category: category,
                    }
                }
            }
            this.loading = true;
            axios.get(this.apiURL, option).then(
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
.foundCharacter {
    height: 40px;
    padding: 5px;
    display: flex;
    align-items: center;
}
</style>