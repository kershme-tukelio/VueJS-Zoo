<template>
    <div>
        Animal List
        <table>
            <tr>
                <th>Species: </th>
                <th>Name: </th>
                <th>Date: </th>
            </tr>
            <tr v-for="({species, name, date}, index) in animals" :key="index">
                <td>{{species}}</td>
                <td>{{name}}</td>
                <td>{{date ? date : "Unknown"}}</td>
                <td><button @click="removeAnimal(index)">Remove</button></td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    name: "AnimalList",
    data() {
        return {
        animals: [
            {
                species: "Cat",
                name: 'Cat1',
                date: new Date()
            },
            {
                species: "Dog",
                name: 'Dog1',
                date: new Date()
            },
            {
                species: "Cow",
                name: 'Cow1',
                date: new Date()
            },
            {
                species: "Snake",
                name: 'Snake1',
                date: new Date()
            },
            {
                species: "Sheep",
                name: 'Sheep1',
                date: new Date()
            },
        ]
        }
    },
    methods: {
        removeAnimal(indexToRemove) {
            this.animals = this.animals.filter((animal, index) => index !== indexToRemove)
        }
    }
}
</script>

<style>

tr {
    border: 1px, solid, grey;
}
td {
    border: 1px, solid, lightblue;
}

</style>
