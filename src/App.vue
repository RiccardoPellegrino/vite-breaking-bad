<template>
  <header>
    <HeaderComponent />
  </header>

  <main>
    <SearchBarComponent />
    <CardListComponent />
  </main>

</template>

<script>

import CardListComponent from './components/CardListComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';
import SearchBarComponent from './components/SearchBarComponent.vue';

export default {
  components: {
    HeaderComponent,
    CardListComponent,
    SearchBarComponent
  }
}
</script>

<style lang="scss" scoped>

</style>


