<template>
    <div class="userScore">
        <div class="innerDiv">
            <p><b>Game No:</b> {{ user_score.user_id }}</p>
            <p><b>Username:</b> {{ user_score.username }}</p>
            <p><b>Score:</b> {{ user_score.score }}</p>
            <p><b>Difficulty:</b> {{ user_score.difficulty_level }}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        user_score:{
            type: Object
        }
    }
}
</script>

<style>
.userScore{
    color: #000;
    margin-top: 30px;
    padding: 0;
    background: #497BA4;
}
.innerDiv{
    padding: 12px 42px;
    display: block;
    transform: translate(15px, 10px);
    transition: .5s;
    background:#88E0C3;
}
.userScore:hover .innerDiv{
    transform: translate(5px, 5px);
    transition: .5s;
}
</style>