<template>
    <div id="StatusLog">
        <div>
            <h1> Log Information </h1>
            <p>Jogador tomou: {{ this.danoMonster }} de dano</p>
            <p>Monstro tomou: {{ this.danoPlayer }} de dano</p>
        </div>
    </div>
</template>

<script>
export default {
    props: ['danoPlayer','danoMonster'],
    
}
</script>

<style scoped>

#StatusLog{
    border: 5px double black;
    display: flex;
    justify-content: center;
}

</style>