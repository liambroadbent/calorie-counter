<template>
  <section id="footer">
    <div class="topbar">
      <h4>logo?</h4>
      <p>Made by Liam Broadbent</p>
    </div>
  </section>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
@import 'assets/css/setup/variables';
#footer { 
  background-color: $grey2;
  min-height:20vh;
  display: flex;
  justify-content: center;
  align-items: center;

  div{
    width: 100%;
    text-align: center;
  }
}
</style>