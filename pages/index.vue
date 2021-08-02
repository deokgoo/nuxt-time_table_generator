<template>
  <div id="time-table-generator">
    <div class="table__container">
      <div class="table__header-wrapper">
        <Header />
      </div>
      <div class="table__content-wrapper">
        <div class="table__content__table">
          <TimeTable :title="title" />
        </div>
        <div class="table__content__editor">
          <Editor :title="title" :on-edit-handler="onEditHandler" />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Header from '../components/header.vue';
import Editor from '../components/editor.vue';
import TimeTable from '../components/timetable.vue';

type Status = {
  title: String;
}

export default Vue.extend({
  components: {
    Header,
    Editor,
    TimeTable
  },
  data ():Status {
    return {
      title: 'Something Title'
    };
  },
  methods: {
    onEditHandler (newTitle: String): void {
      this.title = newTitle;
    }
  }
});
</script>

<style lang="scss" scoped>
#time-table-generator {
  width: 100%;

  .table__container {
    width: 100%;
    display: flex;
    flex-direction: column;

    .table__header-wrapper {
      height: 80px;
    }

    .table__content-wrapper {
      display: flex;
      height: calc(100vh - 80px);

      .table__content__table {
        padding: 40px 0;
        width: 65%;
      }

      .table__content__editor {
        padding: 40px 0;
        width: 25%;
      }
    }
  }
}
</style>
