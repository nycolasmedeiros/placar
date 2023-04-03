<template>
    <button @click="eraseScore">Zerar</button>
</template>

<script>

export default{
    name: 'EraseScore',
    methods:{
        eraseScore() {
            this.$emit('erase')
        }
    }
}


</script>

<style>

</style>