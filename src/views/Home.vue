<template>
    <div class="homeView">
        <h1>Home</h1>
        <div class="gameSetup_app">
            <GameSetup 
                :difficulty_level="difficulty_level" 
                :username="username" 
                :select_err="select_err"
                @selected="changeDifficulty" 
                @enteredUsername='changeUsername'
                class="home_gameSetup"
            />
        </div>
        <div v-if="difficulty_level" class="startButtonDiv">
            <router-link to="/game" class="active">
                <StartButton @checkValidation="checkValidation"/>
            </router-link>
        </div>

        <div v-else>
            <StartButton @checkValidation="checkValidation"/>
        </div>
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
    methods:{
        changeDifficulty(diff_level){
            this.difficulty_level = diff_level
        },
        changeUsername(setup_username){
            this.username = setup_username
        },
        checkValidation(){
            this.select_err = 'Choose a difficulty level.'
            if(this.difficulty_level != '')
            {
                this.select_err = ''

                localStorage.setItem('username', this.username)
                localStorage.setItem('diff_lvl', this.difficulty_level)
            }  
        }
    }
}
</script>

<style>
.home_gameSetup{
    margin-top: 50px;
    margin-bottom: 50px;
}

.gameSetup_app{
  width: 50%;
  margin: auto;
}
.active{
    margin: 0;
    padding: 0;
}
</style>