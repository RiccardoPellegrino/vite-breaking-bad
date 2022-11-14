<template>
  <header>
    <HeaderComponent />
  </header>

  <main>
    <SearchBarComponent />
    <CardListComponent />
    <CardComponent :characters="characterList" />
  </main>

</template>

<script>
import axios from 'axios';
import CardComponent from './components/CardComponent.vue';
import CardListComponent from './components/CardListComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';
import SearchBarComponent from './components/SearchBarComponent.vue';

export default {
  components: {
    HeaderComponent,
    CardListComponent,
    CardComponent,
    SearchBarComponent
  },
  data() {
    return {
      apiURL: 'https://www.breakingbadapi.com/api/characters',
      characterList: [],
      // cinque: [],
    }
  },
  methods: {
    //chiamata per api come metodo
    getCharacters() {
      // this.loading = true;
      axios.get(this.apiURL).then(
        (res) => {
          console.log(res.data)
          this.characterList = [...res.data]
          console.log(this.characterList)
          // this.loading = false;
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


