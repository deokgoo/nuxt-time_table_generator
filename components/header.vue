<template>
  <div id="header">
    {{ title }}
    <button @click="someTest">test</button>
  </div>
</template>

<script lang="ts">
export default {
  data () {
    return {
      title: 'Simple TimeTable Generator'
    };
  },
  created () {

  },
  methods: {
    someTest () {
      localStorage.setItem('someti', 'asdf');
      console.log(localStorage.getItem('someti'));
    }
  }
};
</script>

<style lang="scss" scoped>
#header {
  width: 100%;
  height: 80px;
  display: flex;
  align-items: center;
  padding-left: 24px;
  background-color: black;
  color: white;
  font-size: 30px;
  font-weight: bold;
}
</style>
