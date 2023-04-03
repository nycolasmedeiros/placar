<template>
    <button @click="whistle">Apito</button>
</template>

<script>

export default{
    name: 'GameWhistle',
    methods: {
        whistle() {
            this.$emit('game-whistle')
        }
    }

}


</script>

<style>

</style>