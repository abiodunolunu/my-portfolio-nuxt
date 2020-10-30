<template>
  <div class="title">
    <p>{{ topText }}</p>
    <h1>{{ mainText }}</h1>
  </div>
</template>

<script>
export default {
  props: {
    topText: {
      type: String,
      default: ''
    },
    mainText: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss" scoped>
div.title {
  --color: #2e5090;
  position: relative;
  display: inline-block;
  background: transparent;
  //   background: #fff;
  padding: 5px 5px;
  border-bottom: 1px solid #ccc;
  transition: 300ms ease-in;

  &::after {
    content: "";
    position: absolute;
    background: var(--color);
    left: 0;
    bottom: -4px;
    height: 8px;
    transform: translateX(-50%);
    width: 50%;
    transform: skew(-20deg);
  }

  &:hover {
    transform: scale(1.04);
  }

  h1 {
    font-size: 30px;
    padding: 2px 0;
    text-transform: uppercase;
  }
}

p {
  text-transform: uppercase;
  color: #fff;
  display: inline-block;
  padding: 2px 8px;
  font-size: 12px;
  position: relative;
  z-index: 1;

  &::after {
    content: "";
    position: absolute;
    background: var(--color);
    height: 100%;
    width: 100%;
    top: 0;
    left: 0;
    z-index: -1;
    transform: skew(-20deg);
  }
}
</style>
