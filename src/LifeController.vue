<template>
    <div class="controlBoxLife">
        <div class="controlBoxLifePlayer">    
            <span> LifePlayer </span> 
            <span> LifeMonster </span>
        </div>
        <div class="controlBoxLifePlayer2">
            <div class="LifePlayer"> 
                <div :style="lifeControlPlayer">
                    {{ this.lifePlayer }}
                </div>
            </div>

            <div class="LifeMonster"> 
                <div :style="lifeControlMonster">
                    {{ this.lifeMonster }}
                </div>
            </div>
        </div>
        <div class="controlBoxLifePlayer">     
            <span> {{this.lifePlayer}}% </span>
            <span> {{this.lifeMonster}}% </span>
        </div>        
    </div>
</template>

<script>
export default {
    props: ['lifePlayer','lifeMonster'],
    computed: {
        lifeControlMonster(){
            return {
                backgroundColor: '#00CC00',
                width: this.lifeMonster + '%' 
            }
        },
        lifeControlPlayer(){
            return {
                backgroundColor: '#00CC00',
                width: this.lifePlayer + '%'
            }
        },
    },
    
}
</script>

<style scoped>

.controlBoxLifePlayer{
    display: flex;
    justify-content: space-around;
    color: white;

}

.controlBoxLifePlayer2{
    display: flex;
    justify-content: space-around;
}

.LifePlayer {
    width: 25%;
    border: 3px solid black;

}

.LifeMonster {
    width: 25%;
    border: 3px solid black;
}

.lifeControlPlayer{
    display: none;
}

</style>