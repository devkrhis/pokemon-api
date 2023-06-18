<template>
    <div id="GameControl">
        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
        <link href="https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&display=swap" rel="stylesheet">
        <div class="FourButtonControl">
            <button @click="basicAttack"> Basic Attack </button>
            <button @click="specialAttack"> Special Attack </button>
            <button @click="heal"> Heal </button>
            <button @click="quit"> To give up </button> 
        </div>

    </div>
    
</template>

<script>
export default {
    data(){
        return {
            lifeMonster: 100,
            lifePlayer: 100,
            danoPlayer: 0,
            danoMonster: 0,
            healPlayer: 0,
            healMonster: 0,
        }
    },
    methods:{
        quit(){
            if(confirm("Do you want to give up?") == true){
                this.lifePlayer = 100
                this.$emit('basiclifePlayer', this.lifePlayer)
                this.lifeMonster = 100
                this.$emit('basiclifeMonster', this.lifeMonster)
                this.$emit('quitGame', true)
            }else{
                this.$emit('quitGame', false)
            }
        },
        basicAttack(){
            this.lifePlayer -= this.danoMonster = Math.floor(Math.random() * 10)
            this.lifeMonster -= this.danoPlayer = Math.floor(Math.random() * 10)
            this.$emit('basiclifePlayer', this.lifePlayer)
            this.$emit('basiclifeMonster', this.lifeMonster)
            this.$emit('damageThePlayerTook', this.danoMonster)
            this.$emit('damageTheMonsterTook', this.danoPlayer)
            if(this.danoMonster >= this.lifePlayer){
                this.lifePlayer = 0
                this.$emit('basiclifePlayer', this.lifePlayer)
                alert("O Player perdeu!")
            } 
            if (this.danoPlayer >= this.lifeMonster){
                this.lifeMonster = 0
                this.$emit('basiclifeMonster', this.lifeMonster)
                alert("O Monstro perdeu!")
            }
        },
        specialAttack(){
            this.lifePlayer -= this.danoMonster = Math.floor(Math.random() * 20)
            this.lifeMonster -= this.danoPlayer = Math.floor(Math.random() * 16)
            this.$emit('basiclifePlayer', this.lifePlayer)
            this.$emit('basiclifeMonster', this.lifeMonster)
            this.$emit('damageThePlayerTook', this.danoMonster)
            this.$emit('damageTheMonsterTook', this.danoPlayer)
            if(this.danoMonster >= this.lifePlayer){
                this.lifePlayer = 0
                this.$emit('basiclifePlayer', this.lifePlayer)
                alert("O Player perdeu!")
            } 
            if (this.danoPlayer >= this.lifeMonster){
                this.lifeMonster = 0
                this.$emit('basiclifeMonster', this.lifeMonster)
                alert("O Monstro perdeu!")
            }

        },
        heal(){
            this.lifePlayer += Math.floor(Math.random() * 20)
            this.lifeMonster += Math.floor(Math.random() * 16)
            this.$emit('basiclifePlayer', this.lifePlayer)
            this.$emit('basiclifeMonster', this.lifeMonster)
            this.$emit('healPlayer', this.lifePlayer)
            this.$emit('healMonster', this.lifeMonster)
            if(this.lifePlayer >= 100){
                this.lifePlayer = 100
                this.$emit('basiclifePlayer', this.lifePlayer)
            } 
            if (this.lifeMonster >= 100){
                this.lifeMonster = 100
                this.$emit('basiclifeMonster', this.lifeMonster)
            }
        }
        
    }
    
}
</script>

<style scoped>

.FourButtonControl{
    display: flex;
    justify-content: space-evenly;
    padding-top: 3%;
    padding-bottom: 5%;
}

.FourButtonControl button{
    padding: 1.3em 3em;
    font-size: 12px;
    text-transform: uppercase;
    letter-spacing: 2.5px;
    font-weight: 500;
    color: #000;
    background-color: #fff;
    border: none;
    border-radius: 45px;
    box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease 0s;
    cursor: pointer;
    outline: none;
    font-family: 'Bruno Ace SC', cursive;
}

.FourButtonControl button:hover {
    background-color: #23c483;
    box-shadow: 0px 15px 20px rgba(46, 229, 157, 0.4);
    color: #fff;
    transform: translateY(-7px);
}

.FourButtonControl button:active {
    transform: translateY(-1px);
}

</style>