<template>
  <div class="header">
    <div class="header__main">
      <div>
        MyDevTools
      </div>
      <MottoLine v-bind:motto="mottoData"></MottoLine>
    </div>
  </div>
</template>

<script>
import MottoLine from "./MottoLine.vue";

export default {
  name: "Heading",
  components: {
    MottoLine
  },
  data: () => ({
    mottoData: "Making Life Easier"
  })
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.header {
  color: rgb(60, 43, 107);
  height: 3rem;
  font-size: 2.5rem;

  &__main {
    display: flex;
  }

  display: flex;
  align-items: center;
  padding-top: -1rem;
}
</style>
