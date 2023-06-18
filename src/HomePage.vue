<template>
    <div id="HomePage">
        <h1> Welcome to the Monster Slayer game! </h1>
        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
        <link href="https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&display=swap" rel="stylesheet">
        <div v-if="startgame == false" class="OneButtonControl">
            <button @click="startingGame"> Start Game </button>
            
        </div>
        <div v-else>
            <LifeController
            :lifeMonster="lifeMonster"
            @basiclifeMonster="lifeMonster = $event"
    
            :lifePlayer="lifePlayer"
            @basiclifePlayer="lifePlayer = $event"
            />
    
            <GameControl
            :lifeMonster="lifeMonster"
            @basiclifeMonster="lifeMonster = $event"
            @quitGame="startgame = !$event"
    
            :lifePlayer="lifePlayer"
            @basiclifePlayer="lifePlayer = $event"
            
            :danoPlayer="danoPlayer"
            :danoMonster="danoMonster"
            @damageTheMonsterTook="danoPlayer = $event"
            @damageThePlayerTook="danoMonster = $event"

            />
    
            <status-log
            :danoPlayer="danoPlayer"
            :danoMonster="danoMonster"
            @damageTheMonsterTook="danoPlayer = $event"
            @damageThePlayerTook="danoMonster = $event"/>
            
        </div>

    </div>
    
</template>

<script>
import LifeController from './LifeController.vue';
import GameControl from './GameControl.vue'
import StatusLog from './StatusLog.vue';

export default {
    components: {LifeController, GameControl, StatusLog},
    data(){
        return {
            startgame: false,
            lifePlayer: 100,
            lifeMonster: 100,
            danoPlayer: 0,
            danoMonster: 0,
        }
    },
    methods: {
        startingGame(){
            if(this.startgame == false){
                this.startgame = true
                this.$emit('changeValueGame', true)
                console.log(this.startgame)
            } else {
                this.startgame = false
                this.$emit('changeValueGame', false)
            }
        },
    }
    
}
</script>

<style scoped>

#HomePage {
    font-family: 'Bruno Ace SC', cursive;
}

#HomePage h1 {
    display: flex;
    justify-content: center;
}

#HomePage .OneButtonControl{
    display: flex;
    justify-content: center;
}

button {
    --green: #1BFD9C;
    font-size: 15px;
    padding: 0.7em 2.7em;
    letter-spacing: 0.06em;
    position: relative;
    font-family: inherit;
    border-radius: 0.6em;
    overflow: hidden;
    transition: all 0.3s;
    line-height: 1.4em;
    border: 2px solid var(--green);
    background: linear-gradient(to right, rgba(27, 253, 156, 0.1) 1%, transparent 40%,transparent 60% , rgba(27, 253, 156, 0.1) 100%);
    color: var(--green);
    box-shadow: inset 0 0 10px rgba(27, 253, 156, 0.4), 0 0 9px 3px rgba(27, 253, 156, 0.1);
}

button:hover {
    color: #82ffc9;
    box-shadow: inset 0 0 10px rgba(27, 253, 156, 0.6), 0 0 9px 3px rgba(27, 253, 156, 0.2);
}

button:before {
    content: "";
    position: absolute;
    left: -4em;
    width: 4em;
    height: 100%;
    top: 0;
    transition: transform .4s ease-in-out;
    background: linear-gradient(to right, transparent 1%, rgba(27, 253, 156, 0.1) 40%,rgba(27, 253, 156, 0.1) 60% , transparent 100%);
}

button:hover:before {
    transform: translateX(15em);
}

</style>