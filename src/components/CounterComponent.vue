<template>
    <div v-html="`Found ${store.characterList.length} characters`" class="foundCharacter fw-bold bg-dark text-white ">
    </div>
</template>

<script>
import { store } from '../store'
export default {
    name: 'CounterComponent',
    data() {
        return {
            store
        }
    }
}
</script>

<style lang="scss" scoped>

</style>