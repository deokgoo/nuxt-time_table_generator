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
          <Editor
            :title="title"
            :time-table-datas="timeTableDatas"
            :on-edit-handler="onEditHandler"
          />
        </div>
      </div>
      <div class="d-flex justify-content-center my-5">
        <button type="button" class="btn btn-outline-dark">
          Download
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Header from '../components/header.vue';
import Editor from '../components/editor.vue';
import TimeTable from '../components/timetable.vue';

type TimeTableData = {
  start: string;
  end: string;
  content: string;
};

type Status = {
  title: String;
  timeTableDatas: TimeTableData[];
};

export default Vue.extend({
  components: {
    Header,
    Editor,
    TimeTable
  },
  data (): Status {
    return {
      title: 'Something Title',
      timeTableDatas: [
        {
          start: '0820',
          end: '0900',
          content: 'test1'
        },
        {
          start: '0900',
          end: '1100',
          content: 'test2'
        }
      ]
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
      // min-height: calc(100vh - 80px);

      .table__content__table {
        padding-top: 40px;
        width: 65%;
      }

      .table__content__editor {
        padding-top: 40px;
        width: 25%;
      }
    }
  }
}
</style>
