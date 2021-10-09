<template>
  <div class="repeater">
    <h2>API Test</h2>
    <label>
      Enter in a valid API address to see the response.
    </label>
    <div class="repeater__inputs">
    
      <div class="repeater__inputs stack">
        <label v-on:click="resetReplaceText">API Address</label>
        <button v-on:click="getData">Get Data</button>
        <input v-model="apiString" />
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
import axios from 'axios'

const api_string = "https://my-json-server.typicode.com/typicode/demo/posts";

export default {
  name: "APITest",
  data: () => ({
    apiString: api_string,
    response: null
  }),
  methods: {
   getData: function(){
     const instance = axios.create({
        baseURL: this.apiString,
        timeout: 1000
      });
      instance.get().then((response) =>{
        this.response = JSON.stringify(response.data, null, 2)
      },(err)=>{
        this.response = JSON.stringify(err, null, 2)
      })
    },
    copyResult() {
      navigator.clipboard.writeText(this.result);
    }
  },
  computed: {
    result: function() {
      return this.response
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
