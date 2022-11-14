<template>
    <div class="container">
        <select class="form-select form-select-lg mb-3 myselect mt-3" aria-label=".form-select-lg example">
            <option selected>Select category</option>
            <option value="1">Dead</option>
            <option value="2">Alive</option>
            <option value="3">Presumed dead</option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'SearchBarComponent'
}
</script>

<style lang="scss" scoped>
.myselect {
    width: 200px;

}
</style>