<template>
    <button @click="toggleShowScoreHistory" class="btn_toggleShowScoreHistory">
        <span v-if="showScoreHistory">Hide Score History</span>
        <span v-else>Show Score History</span>
    </button>
</template>

<script>
export default {
    props: ['showScoreHistory'],
    methods:{
        toggleShowScoreHistory(){
            this.$emit('toggleShowScoreHistory')
        }
    }
}
</script>

<style>
.btn_toggleShowScoreHistory{
    background: hsl(340deg 100% 32%);
    border-radius: 12px;
    border: none;
    padding: 0;
    cursor: pointer;
    outline-offset: 4px;
}
.btn_toggleShowScoreHistory span{
    display: block;
    padding: 12px 42px;
    border-radius: 12px;
    font-size: 1.25rem;
    background: hsl(345deg 100% 47%);
    color: white;
    transform: translateY(-6px);
}
.btn_toggleShowScoreHistory:hover span{
    transform: translateY(-8px);

}
.btn_toggleShowScoreHistory:active span {
    transform: translateY(-2px);
}
</style>