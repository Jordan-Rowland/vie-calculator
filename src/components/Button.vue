<template>
  <div @click="clicked" class="app-button column col-4">
    <p>
    {{ digit }}
    </p>
  </div>
</template>

<script>
/* jshint esversion: 9 */
export default {
  name: 'appbutton',
  props: ["digit"],
  data() {
    return {

    };
  },
  methods: {
    clicked() {
      // console.log('[button] clicked', this.digit)
      this.$emit('parentClicked', this.digit)
    }
  }
};
</script>

<style scoped>
div:hover {
  cursor: pointer;
}

p {
  height: 65px;
  padding-top: 20px;
  /*border: 1px solid red;*/
}

.app-button {
  border: 1px solid black;
  border-radius: 10px;
  box-shadow: none;
  width: 75px;
  height: 65px;
  margin: auto;
  background-color: #3f99aa;
  margin-bottom: 13px;
}

.app-button:hover, button:hover {
  cursor: pointer;
}
</style>
