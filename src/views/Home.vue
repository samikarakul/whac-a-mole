<template>
    <h1>Home</h1>
    <div class="gameSetup_app">
        <GameSetup 
            :difficulty_level="difficulty_level" 
            :username="username" 
            :select_err="select_err"
             @selected="changeDifficulty" 
             @enteredUsername='changeUsername'
        />
    </div>
    <div v-if="difficulty_level">
        <router-link to="/game">
            <StartButton @checkValidation="checkValidation"/>
        </router-link>
    </div>

    <div v-else>
        <StartButton @checkValidation="checkValidation"/>
    </div>
    
    

</template>

<script>
import GameSetup from '../components/GameSetup.vue'
import StartButton from '../components/StartButton.vue'

export default {
    components: {GameSetup, StartButton},
    data(){
        return{
            difficulty_level: '',
            username: '',
            select_err:'',
        }
    },
    // mounted(){
    //     this.difficulty_level = ''
    //     this.username= ''
    // },
    methods:{
        changeDifficulty(diff_level){
            this.difficulty_level = diff_level
            if(this.select_err == 'Choose a difficulty level.') 
            {
                this.username = ' '
                this.username = ''
            }

        },
        changeUsername(setup_username){
            this.username = setup_username
        },
        checkValidation(){
            this.select_err = 'Choose a difficulty level.'
            if(this.difficulty_level != '')
            {
                if(this.username == '') this.username = 'Anonym'
                this.select_err = ''

                localStorage.setItem('username', this.username)
                localStorage.setItem('diff_lvl', this.difficulty_level)
            }  
        }
    }
}
</script>

<style>
.gameSetup_app{
  width: 50%;
  margin: auto;
}
</style>