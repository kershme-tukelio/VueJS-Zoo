<template>
    <div>
        Animal List
        <animal-form @add-animal="addAnimal"></animal-form>
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
                <td><button @click="moveToTop(index)">Move to top</button></td>
            </tr>
        </table>
    </div>
</template>

<script>
import AnimalForm from './AnimalForm.vue';

export default {
    name: "AnimalList",
    components: {
        AnimalForm
    },
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
        },
        moveToTop(indexToMove) {
            const animalToMove = this.animals[indexToMove];
            this.removeAnimal(indexToMove);
            this.animals.unshift(animalToMove);
            console.log(this.animals);
        },
        addAnimal(newAnimal) {
            this.animals.push(newAnimal);
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
