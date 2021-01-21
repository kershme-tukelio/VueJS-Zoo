<template>
    <div>
        Animal List
        <animal-form @add-animal="addAnimal" :sectors="sectors"></animal-form>
        <table>
            <tr>
                <th>Species: </th>
                <th>Name: </th>
                <th>Date: </th>
                <th>Sector: </th>
            </tr>
            <tr v-for="({species, name, date, sector}, index) in animals" :key="index">
                <td>{{species}}</td>
                <td>{{name}}</td>
                <td>{{date ? date : "Unknown"}}</td>
                <td>{{sector}}</td>
                <td><button @click="moveToTop(index)">Move to top</button></td>
                <td><button @click="removeAnimal(index)">Remove</button></td>
            </tr>
        </table>
        <animal-sectors :sectors="sectors" @sector-click="showAnimalsForSector" ></animal-sectors>
    </div>
</template>

<script>
import AnimalForm from './AnimalForm.vue';
import AnimalSectors from './AnimalSectors.vue'

export default {
    name: "AnimalList",
    components: {
        AnimalForm,
        AnimalSectors
    },
    data() {
        return {
            sectors: ['dogs', 'snakes', 'cats', 'domestic', 'wild', 'birds', 'bugs'],
            animals: [
            {
                species: "Cat",
                name: 'Cat1',
                date: new Date(),
                sector: "cats"
            },
            {
                species: "Dog",
                name: 'Dog1',
                date: new Date(),
                sector: "dogs"
            },
            {
                species: "Cow",
                name: 'Cow1',
                date: new Date(),
                sector: "domestic"
            },
            {
                species: "Snake",
                name: 'Snake1',
                date: new Date(),
                sector: "snakes"
            },
            {
                species: "Sheep",
                name: 'Sheep1',
                date: new Date(),
                sector: "domestic"
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
        },
        showAnimalsForSector(sector) {
            const animalsToShow = this.animals.reduce((acc, current) => {
                if(current.sector === sector) {
                    acc += " " + current.name;
                }
                return acc;
            }, "")
            alert(animalsToShow);
        }
    }
}
</script>

<style>

tr {
    border: 1px, solid, black;
}
td {
    border: 1px, solid, green;
}

</style>
