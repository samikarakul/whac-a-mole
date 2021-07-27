<template>
    <div class="gameSetup">
        <p v-if="select_err">{{ select_err }}</p>

        <input v-model="username" @keyup="usernameEntered" class="gameSetup_username"/>

        <select v-model="difficulty_level" @change="difficultySelected" class="gameSetup_difficulty_level" id="dropdown_difficultyLevel">
            <option disabled value="">Please select one</option>
            <option value="easy">Easy</option>
            <option value="medium">Medium</option>
            <option value="hard">Hard</option>
        </select>
    </div>
</template>

<script>
export default {
    props: ['difficulty_level', 'username', 'select_err'],
    methods: {
        difficultySelected(){
            this.$emit('selected', this.difficulty_level)
        },
        usernameEntered(){
            this.$emit('enteredUsername', this.username)
        },
    }
}
</script>

<style>
.gameSetup_username, .gameSetup_difficulty_level{
    display: block;
    margin-top: 20px;
    margin-bottom: 20px;
    height: 40px;
}

.gameSetup_username{
    border: none;
    width: 100%;

}
.gameSetup_username:focus{
    outline: none !important;
    border: 2px solid rgb(109, 109, 172);
    box-shadow: 0 0 10px #719ECE;
    margin-bottom: -2px;
    margin-top: -2px;
}

.gameSetup_difficulty_level{
    border: none;
    outline: none !important;
    font-family: Andale Mono, monospace;
    font-size: 15px;
    width: 200px;

}
#dropdown_difficultyLevel option{
    width: 200px !important;
}
</style>