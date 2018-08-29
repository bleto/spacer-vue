<template>
  <main class="claimWrapper">
    <h1 class="claim">Spacer</h1>
    <p class="subclaim">
        Ex sint ullamco aliqua dolore. <br>Do eu cupidatat magna cupidatat incididunt laborum irure et.
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

      @media (min-width: 768px) {
        font-size: 80px;
      }
      @media (min-width: 1024px) {
        font-size: 100px;
      }
  }
  .subclaim{
      margin: 20px 0 0 0;
      font-size: 13px;
      font-weight: 400;

      @media (min-width: 768px) {
        font-size: 17px;
        width: 500px;
        line-height: 1;
        letter-spacing: 1px;
      }
  }
</style>