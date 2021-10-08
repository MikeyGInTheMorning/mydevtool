<template>
  <div class="repeater">
    <h2>Line Repeater</h2>
    <label>
      Type a sentence below using [[i]] in the sentene to repeat with the loop.
    </label>
    <div class="repeater__inputs">
      <div class="repeater__inputs--small">
        <div class="stack">
          <label>Starting Index</label>
          <input v-model="startIndex" />
        </div>

        <div class="stack">
          <label>Iterations</label>
          <input v-model="iterations" />
        </div>

        <div class="stack">
          <label
            >Replace Text
            <button class="resetBtn" @click="resetReplaceText">Reset</button>
          </label>
          <input v-model="replaceText" />
        </div>
      </div>

      <div class="repeater__inputs stack">
        <label v-on:click="resetReplaceText">Text To Repeat</label>
        <input v-model="textToRepeat" />
      </div>
    </div>

    <div class="repeater__outputs stack">
      <label
        >Result<button class="copyBtn" @click="copyResult">Copy</button>
      </label>
      <textarea class="repeater__outputs--result-box" v-model="result" />
    </div>
  </div>
</template>

<script>
const iterator_string = "(iterator)";
export default {
  name: "LineCopier",
  data: () => ({
    startIndex: 0,
    iterations: 10,
    replaceText: iterator_string,
    textToRepeat: ""
  }),
  methods: {
    resetReplaceText: function() {
      console.log("hi");
      this.replaceText = iterator_string;
    },
    copyResult() {
      navigator.clipboard.writeText(this.result);
    }
  },
  computed: {
    result: function() {
      var res = "";
      if(this.startIndex <= this.iterations)
      for (var i = this.startIndex; i < this.iterations; i++) {
        var replaceVal =
          this.replaceText == iterator_string ? i : this.replaceText;

        var textToRepeat = this.textToRepeat;
        res += textToRepeat.replaceAll("[[i]]", replaceVal) + "\n";
      }
      return res.slice(0, -1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.resetBtn {
  color: maroon;
  border: none;
  background: none;
  margin-left: 5rem;
}

.copyBtn {
  color: lightgreen;
  border: none;
  background: none;
  margin-left: 5rem;
}

.stack {
  padding: 1rem 0 1rem 0;
  display: flex;
  flex-direction: column;
  justify-self: center;

  label {
    display: flex;
    justify-self: flex-start;
    // background:blue;
    padding: 0.5rem;
  }
}

.repeater {
  flex: 1;
  //background: grey;

  &__outputs {
    &--result-box {
      height: 12rem;
    }
  }

  &__inputs {
    display: flex;
    flex-direction: column;

    &--small {
      display: flex;
      align-items: center;
      justify-content: center;
      //background: green;
    }
  }
}
</style>
