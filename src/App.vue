<template>
  <header>
    <HeaderComponent />
  </header>

  <main>

    <CardListComponent />
  </main>

</template>

<script>

import CardListComponent from './components/CardListComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';


export default {
  components: {
    HeaderComponent,
    CardListComponent,

  }
}
</script>

<style lang="scss" scoped>

</style>


