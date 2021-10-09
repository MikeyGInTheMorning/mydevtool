<template>
  <div class="motto__lines">
    <div
      class="motto__lines__item"
      v-for="mottoLine in mottoSplit"
      :key="mottoLine.id"
    >
      {{ mottoLine }}
    </div>
  </div>
</template>

<script>
export default {
  name: "MottoLine",
  props: {
    motto: String
  },
  computed: {
    mottoSplit: function() {
      return this.motto.split("\n");
    }
  }
};
</script>

<style scoped lang="scss">
.motto {
  &__lines {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;

    padding-top: 0.1rem;
    padding-left: 0.2rem;

    &__item {
      font-weight: 900;
      font-size: 0.6rem;
    }
  }
}
</style>
