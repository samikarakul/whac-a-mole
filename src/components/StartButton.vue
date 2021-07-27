<template>
    <button 
        class="btn_start btnStart_beginning" 
        @mouseenter="btnStart_mouseEnter"
        @mouseleave="btnStart_mouseleave"
        @mousedown="btnStart_mouseDown"
    >
        Start
    </button>
    
    <!-- <router-link 
        to="/game"
        class="btn_start btnStart_beginning" 
        @mouseenter="btnStart_mouseEnter"
        @mouseleave="btnStart_mouseleave"
        @mousedown="btnStart_mouseDown"
    >
        Start
    </router-link> -->
</template>

<script>
export default {
    methods: {
        btnStart_mouseEnter(e){
            e.target.classList.add('btn_mouseEnter')
            e.target.classList.remove('btnStart_beginning')
        },
        btnStart_mouseleave(e){
            e.target.classList.add('btnStart_beginning')
            e.target.classList.remove('btn_mouseEnter')
        },
        btnStart_mouseDown(e){
            e.target.classList.add('btnStart_mouseDown')
            document.addEventListener(
                'mouseup', () => {
                    e.target.classList.remove('btnStart_mouseDown')
                    this.$emit('checkValidation')
                }
            )
        }
    }
}
</script>

<style>
.btnStart_beginning{
    background: linear-gradient(to right,#DAA45A, #E02F20  ) !important;
}
.btn_start{
    color: #fff;
    width: 125px;
    height: 70px;
    border-radius: 20%;
    border: none;
    box-shadow: 5px 7px 2px #6a6969;
    font-size: 35px;
}
.btn_mouseEnter{
    background: linear-gradient(to right,#E2D664,#D8970C) !important;
    box-shadow: 4px 4px 2px #6a6969 !important;
    color: #000;
}
.btnStart_mouseDown{
    background: linear-gradient(to right,#E2D664,#D8970C) !important;
    box-shadow: inset 4px 4px 2px #6a6969 !important;
}
</style>