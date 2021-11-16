<template>
  <div class="claimWrapper">
    <h1 class="claim">Spacer with Hello Roman</h1>
    <p class="subclaim">Begin your journey through our amazing galaxy,
       and discover places you never even heard of.</p>
    <p class="subclaim">Type anything space-related to start</p>
  </div>
</template>

<script>
export default {
  name: 'Claim',
};
</script>

<style lang="scss" scoped>

.claimWrapper{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: #40a4be;
}

.claim{
  font-size: 55px;
  margin: 0;
  text-transform: uppercase;
  font-weight: bold;
}

.subclaim{
  margin: 20px 0 0 0;
  font-size: 15px;
  font-weight: bold;
}
</style>
