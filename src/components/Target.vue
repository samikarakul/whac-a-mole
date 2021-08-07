<template>
<div 
    class="target"
    :style="{left: x + 'px',top: y + 'px',}"
    @click="targetFounded"
>
    <img src="../assets/mole.png" class="mole"/>

</div>
</template>

<script>
export default {
    props: ['difficulty_level'],
    data(){
        return{
            x: 50 + Math.random() * 1500,
            y: 50 + Math.random() * 200,   
            timer: null,
            countdown: 3000,
            lives: 3,
        }
    },
    methods: {
        startTimer(){
            this.countdown = 3000
            if(this.difficulty_level == 'hard') 
            {
                this.countdown = 1000
            }
            else if (this.difficulty_level == 'medium') 
            {
                this.countdown = 2000
            }
            this.x= 50 + Math.random() * 1500
            this.y= 50 + Math.random() * 200
            this.timer = setInterval(() => {
                if(this.countdown != 0)
                {
                    this.countdown -= 10
                }
                else{
                    this.stopTimer()
                }  
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            if(this.lives > 1) 
            {
                this.lives -=1
                this.startTimer()
            }
            this.$emit('dicreaseLive')

        },
        targetFounded()
        {
            this.$emit('targetFounded')
            clearInterval(this.timer)
            this.startTimer()
        }
    },
    mounted(){
        
        this.startTimer()
    },
}
</script>

<style>
.target{
    width: 150px;
    height: 100px;
    background: #000;
    /* border-radius: 25px; */
    border-radius: 50%;
    text-align: center;
    color: white;
    position: relative;
    border: 2px solid black;
}
.mole{
    margin-top: -30%;
}

</style>