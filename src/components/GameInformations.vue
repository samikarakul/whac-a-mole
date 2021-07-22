<template>
    <p>Lives: {{ lives}}</p>
    <p>Score: {{ score }}</p>
    <p>Username: {{ username }}</p>
</template>

<script>
export default {
    props: ['lives', 'score', 'username']
}
</script>

<style>

</style>