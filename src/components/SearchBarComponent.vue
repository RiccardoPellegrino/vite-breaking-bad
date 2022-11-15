<template>
    <div class="container d-flex mb-3 justify-content-center mt-5">
        <form class="row row-cols-lg-auto g-3 align-items-center" @submit.prevent="searchCharacter">
            <!-- <div class="col-12">
                <label class="visually-hidden" for="characterName">Cerca nome</label>
                <input type="text" class="form-control" placeholder="Cerca nome">
            </div> -->

            <div class="col-12">

                <select class="form-select" v-model="search">
                    <option value="">Choose...</option>
                    <option :value="category" v-for="(category, index) in categoryOptions" :key="index">{{ category }}
                    </option>

                </select>
            </div>

            <div class="col-12">
                <button type="submit" class="btn btn-primary">Cerca</button>
            </div>

            <div class="col-12">
                <button type="reset" class="btn btn-danger" @click="resetSearch">Reset</button>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    name: 'SearchBarComponent',
    data() {
        return {
            categoryOptions: [
                'Breaking Bad',
                'Better Call Saul'
            ],
            search: ""
        }
    },
    methods: {
        searchCharacter() {
            this.$emit("filterChar", this.search)

        },
        resetSearch() {
            this.search = "";
            this.$emit("filterChar", this.search)
        }
    }

}
</script>

<style lang="scss" scoped>
.myselect {
    width: 200px;

}
</style>