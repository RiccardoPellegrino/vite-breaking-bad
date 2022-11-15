<template>
    <SearchBarComponent @filterChar="getCharacters" />
    <section class="container card-container bg-white">
        <div class="pt-3">
            <div class="container mt-2 mb-2">
                <CounterComponent />
            </div>
        </div>
        <CardComponent :characters="store.characterList" :loading="store.loading" />
    </section>
</template>

<script>
import axios from 'axios'
import CardComponent from './CardComponent.vue'
import SearchBarComponent from './SearchBarComponent.vue'
import { store } from '../store';
import CounterComponent from './CounterComponent.vue';
export default {
    components: {
        CardComponent,
        SearchBarComponent,
        CounterComponent
    },
    name: 'CardListComponent',
    data() {

        return {
            store,
            endPoint: '/characters'
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
            store.loading = true;
            const url = store.apiURL + this.endPoint
            axios.get(url, option).then(
                (res) => {
                    console.log(res.data)
                    store.characterList = [...res.data]
                    console.log(store.characterList)
                    store.loading = false;
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