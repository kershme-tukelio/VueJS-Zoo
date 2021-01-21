<template>
    <ul>
        <li v-for="(sector, index) in sectors" :key="index" >{{sector}}
            <button @click="emitClick(sector)">View content</button>
        </li>
    </ul>
</template>

<script>
export default {
    props: ['sectors'],
    methods: {
        emitClick(sectorToShow) {
            this.$emit('sector-click', sectorToShow);
        }
    }
}
</script>

<style>

</style>
