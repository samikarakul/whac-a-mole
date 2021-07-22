<template>
    <button 
        class="playButton playButtonBeginning" 
        @click="startGame" 
        @mousedown="playMouseDown"
        @mouseover="playMouseOver"
        @mouseout ="playMouseOut"
    >
        Play
    </button>
</template>

<script>
export default {
    props: ['gameOver'],
    updated()
    {
        if(this.$props.gameOver){
            document.getElementsByClassName('playButton')[0].classList.add('playButtonBeginning')
            document.getElementsByClassName('playButton')[0].classList.remove('playButtonDisabled') 
        } 
    },
    methods: {
        playMouseDown(e)
        {
            e.target.classList.add('playButtonMouseDowned')
            e.target.classList.remove('playButtonBeginning')
            document.addEventListener(
                "mouseup",
                () => {
                    e.target.classList.add('playButtonBeginning')
                    e.target.classList.remove('playButtonMouseDowned')
                },
                // { once: true }
            )
        },
        playMouseOver(e){
            if(! e.target.classList.contains('playButtonDisabled'))
            {
            e.target.classList.add('playButtonHovered')
            e.target.classList.remove('playButtonBeginning')
            }
        },
        playMouseOut(e){
            e.target.classList.add('playButtonBeginning')
            e.target.classList.remove('playButtonHovered')
        },
        startGame(e){
            e.target.classList.add('playButtonDisabled')
            e.target.classList.remove('playButtonBeginning')

            this.$emit('startGame')
        },
    }
}
</script>

<style>
.playButton{
  width: 100px;
  height: 50px;
  border: none;
  border-radius: 20%;
  color:#000;
  font-size: 20px;
  font-family: Rockwell;
  margin-bottom: 30px;
}

.playButton[disabled]{
  color: rgb(147, 137, 137);
}
.playButton:hover{
  background-image: linear-gradient(to right,#42bd42, rgb(137, 194, 66));
}
.userScoreHistory{
  width: 50%;
  margin-right: auto;
  margin-left: auto;
}
.playButtonBeginning{
  background: linear-gradient(to right,#81e094, rgb(149, 214, 75)) !important;
  box-shadow: 5px 5px 2px #6a6969;
}
.playButtonDisabled{
  background: linear-gradient(to right,#b6bbb6, rgb(221, 230, 210)) !important;
  box-shadow: 2px 2px 10px  #6a6969;
}
.playButtonHovered{
  background: linear-gradient(to right,#42bd42, rgb(137, 194, 66)) !important;
}
.playButtonMouseDowned{
  background: radial-gradient(closest-side,#42bd42, #318e31) !important;
  box-shadow: 0px 0px 0px;
}
</style>