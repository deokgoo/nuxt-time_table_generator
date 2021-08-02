<template>
  <div id="time-table">
    <div class="title">
      {{ title }}
    </div>
    <div class="content">
      <div class="tmp" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'TimeTable',
  props: {
    title: {
      type: String,
      default: 'Title',
      require: true
    }
  }
};
</script>

<style lang="scss" scoped>
#time-table {
  display: flex;
  flex-direction: column;

  .title {
    height: 10%;
    text-align: center;
    font-size: 36px;
    font-weight: bold;
  }

  .content {
    display: flex;
    justify-content: center;
    padding: 40px 0;

    .tmp {
      background-color: paleturquoise;
      border-radius: 50%;
      height: 800px;
      width: 800px;
      min-height: 800px;
      min-width: 800px;
    }
  }
}
</style>
