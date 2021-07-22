<template>
  <div class="currentSetupInformation">
      <p>Username: {{ username }}</p>
      <p>Dİfficulty Level: {{ difficulty_level }}</p>
  </div>
</template>

<script>
export default {
    props: ['username', 'difficulty_level']
}
</script>

<style>
.currentSetupInformation p{
    display: block;
}
</style>