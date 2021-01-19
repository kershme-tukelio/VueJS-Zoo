<template>
    <div>
        Animal List
        <table>
            <tr>
                <th>Vrsta: </th>
                <th>Ime: </th>
                <th>Datum: </th>
            </tr>
            <tr v-for="({species, name, date}, index) in animals" :key="index">
                <td>{{species}}</td>
                <td>{{name}}</td>
                <td>{{date}}</td>
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
