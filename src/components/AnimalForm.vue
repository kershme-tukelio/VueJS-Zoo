<template>
    <form @submit.prevent="onSubmit">
        <label for="species">Species: </label>
        <input required v-model="species" id="species" type="text" placeholder="species"><br/>

        <label for="name">Name: </label>
        <input required v-model="name" id="name" type="text" placeholder="name"><br/>

        <label for="date">Date: </label>
        <input required v-model="date" id="date" type="date" placeholder="Date of birth"><br/>

        <label for="sector">Sector: </label>
        <select required v-model="sector" name="sector" id="sector">
            <option v-for="(sector, index) in sectors" :key="index">{{sector}}</option>
        </select>
        <button type="submit">Add animal</button>
    </form>
</template>

<script>
export default {
    name: "AnimalForm",
    data() {
        return {
            species: "",
            name: "",
            date: "",
            sector: ""
        }
    },
    props: ['sectors'],
    methods: {
        onSubmit() {
            this.$emit('add-animal', {
                species: this.species,
                name: this.name,
                date: new Date(this.date),
                sector: this.sector
            })
            this.species = "";
            this.name = "";
            this.date = "";
            this.sector = "";
        }
    }
}
</script>

<style>

</style>
