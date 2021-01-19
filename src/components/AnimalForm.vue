<template>
    <form @submit.prevent="onSubmit">
        <label for="species">Species: </label>
        <input v-model="species" id="species" type="text" placeholder="species"><br/>

        <label for="name">Name: </label>
        <input v-model="name" id="name" type="text" placeholder="name"><br/>

        <label for="date">Date: </label>
        <input v-model="date" id="date" type="date" placeholder="Date of birth"><br/>

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
            date: ""
        }
    },
    methods: {
        onSubmit() {
            this.$emit('add-animal', {
                species: this.species,
                name: this.name,
                date: new Date(this.date)
            })
        }
    }
}
</script>

<style>

</style>
