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
import CounterComponent from './components/CounterComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';


export default {
  components: {
    HeaderComponent,
    CardListComponent,
    CounterComponent
  }
}
</script>

<style lang="scss" scoped>

</style>


