<template>
    <button @click="playRandomSounds" :disabled="isPlaying">???</button>
</template>

<script>
export default{
    name: 'RandomSounds',
    data() {
        return {
            sounds: [
                {
                    file: 'a-bomba.mp3'
                },
                {
                    file: 'calma.mp3'
                },
                {
                    file: 'cavalo.mp3'
                },
                {
                    file: 'demais.mp3'
                },
                {
                    file: 'ele-gosta.mp3'
                },
                {
                    file: 'pare.mp3'
                },
                {
                    file: 'tome.mp3'
                },
                {
                    file: 'uepa.mp3'
                },
                {
                    file: 'xi.mp3'
                }
            ],
            isPlaying: false
        }
    },
    methods:{
        playRandomSounds(){
            this.isPlaying = true

            const randomSoundIndex = Math.floor(Math.random() * this.sounds.length-1)
            const randomSound = this.sounds[randomSoundIndex]

            const audio = new Audio(`/instants/${randomSound.file}`)
            audio.play()
            setTimeout(() => {
                this.isPlaying = false
            }, 1000)
        }
    }
}


</script>

<style>

</style>