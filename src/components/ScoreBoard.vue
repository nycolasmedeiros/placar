<template>
    <div>
        <div>
            <span v-if="!isTeamNameToggled" :class="$style.teamName" @click="showTeamNameInput()">{{ teamName }}</span>
            <input v-else paceholder="Nome do Time" ref="teamName" :class="$style.teamName" @blur="isTeamNameToggled = !isTeamNameToggled" @input="(e) => teamName = e.target.value" />
        </div>
        <div :class="$style.scoreCount">
            <button  :class="$style.minusBtn" @click="decrease"> - </button>
            <h2 :class="$style.scoreCount"> {{ score }} </h2>
            <button :class="$style.plusBtn" @click="increase"> + </button>
            
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ScoreBoard',
        props: {
            score: {
                type: Number,
                default: 0
            },
            scoreName: {
                type: String,
                default: ''
            }
        },
        data() {
            return {
                isTeamNameToggled: false,
                teamName: "Nome"
            }
        },
        methods:{
            increase(){ 
                this.$emit('increase', this.scoreName)          
            },
            decrease(){
                this.$emit('decrease', this.scoreName)
            },
            showTeamNameInput() {
                this.isTeamNameToggled = !this.isTeamNameToggled;

                setTimeout( () => {
                    this.$refs.teamName.focus()
                } , 200)
            },
            teamInput() {
                this.isTeamNameToggled = !this.isTeamNameToggled;

      setTimeout( () => {
        this.$refs.teamName.focus()
      } , 200)
            }
        }
    }
</script>

<style lang="scss" module>

.teamName {
    font-size: 40px;
    top: 10px;
    background-color: transparent;
}

.scoreCount {
    display: flex;
    flex-direction: row;
    align-items: center;
    align-self: center;
    justify-content: center;
    height: 300px;
    width: 280px;
}
.minusBtn, .plusBtn {
    font-family: 'Montserrat';
    font-weight: 700;
    font-size: 40px;
    text-transform: uppercase;
    top: 0;

    width: 80px;
    height: 50px;

    left: 22%;

    padding: 0;
    border: none;
    border-radius: 50%;
}

</style>