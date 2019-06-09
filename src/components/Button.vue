<template>
  <div @click="clicked">
    <p>
    {{ number }}
    </p>
  </div>
</template>

<script>
/* jshint esversion: 9 */
export default {
  name: 'appbutton',
  props: ["number"],
  data() {
    return {

    };
  },
  methods: {
    clicked() {
      this.$emit('parentClicked', this.number)
    }
  }
};
</script>

<style scoped>
div:hover {
  cursor: pointer;
}

p {
  margin-top: 10px;
}
</style>
