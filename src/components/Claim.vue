<template>
  <main class="claimWrapper">
    <h1 class="claim">Spacer</h1>
    <p class="subclaim">
        jakieś info bla bl bal
    </p>
  </main>
</template>
<script>
  export default {
    name: 'Claim'
  };
</script>

<style lang="scss" scoped>
  .claimWrapper{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center
  }
  .claim{
      margin: 0;
      font-size: 50px;
  }
  .subclaim{
      margin: 20px 0 0 0;
      font-size: 13px;
  }
</style>