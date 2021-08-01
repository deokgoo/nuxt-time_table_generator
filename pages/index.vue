<template>
  <div id="time-table-generator">
    <div class="table__container">
      <div class="table__header-wrapper">
        <Header v-if="trigger" />
      </div>
      <div class="table__content-wrapper">
        <div class="table__content__table">
          <TimeTable />
        </div>
        <div class="table__content__editor">
          <Editor />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Header from '../components/header.vue';
import Editor from '../components/editor.vue';
import TimeTable from '../components/timetable.vue';

export default {
  components: {
    Header,
    Editor,
    TimeTable
  },
  data () {
    return {
      trigger: true
    };
  }
};
</script>

<style lang="scss" scoped>
#time-table-generator {
  width: 100%;

  .table__container {
    width: 100%;
    display: flex;
    flex-direction: column;
  }

  .table__content-wrapper {
    display: flex;
    .table__content__table { width: 65%; }
    .table__content__editor { width: 25%; }
  }
}
</style>
