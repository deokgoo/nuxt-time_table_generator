<template>
  <div id="editor">
    <form>
      <div class="form-group">
        <label for="editor__title">Title</label>
        <input
          id="editor__title"
          v-model="editTitle"
          class="form-control"
          type="text"
          aria-describedby="titleHelp"
          placeholder="Enter title"
          @keyup="onEdit"
        >
        <small id="titleHelp" class="form-text text-muted">
          We'll never share your title with anyone else.
        </small>
      </div>
    </form>
    <div class="editor__table">
      <table class="table text-center">
        <thead class="thead-dark">
          <tr>
            <th scope="col">
              start
            </th>
            <th scope="col">
              end
            </th>
            <th scope="col">
              content
            </th>
            <th scope="col">
              setting
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="table in timeTableDatas" :key="table.start">
            <td>{{ table.start }}</td>
            <td>{{ table.end }}</td>
            <td>{{ table.content }}</td>
            <td>@mdo</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="editor__insert">
      <table class="table text-center editor__insert__table">
        <thead class="thead-dark">
          <tr>
            <th scope="col">
              start
            </th>
            <th scope="col">
              end
            </th>
            <th scope="col">
              content
            </th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><input type="text"></td>
            <td><input type="text"></td>
            <td><input type="text"></td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="editor__controller">
      <button type="button" class="btn btn-info">add</button>
      <button type="button" class="btn btn-light">clear</button>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

type Status = {
  editTitle: String;
};

export default Vue.extend({
  props: {
    title: {
      type: String,
      default: 'Something Title'
    },
    onEditHandler: {
      type: Function,
      default: (title: String) => {
        console.log(title);
      }
    },
    // eslint-disable-next-line vue/require-default-prop
    timeTableDatas: {
      type: Array
    }
  },
  data (): Status {
    return {
      editTitle: ''
    };
  },
  created () {
    this.editTitle = this.title;
  },
  methods: {
    onEdit () {
      if (!this.onEditHandler) {
        return;
      }
      this.onEditHandler(this.editTitle);
    }
  }
});
</script>

<style lang="scss" scoped>
#editor {
  display: flex;
  flex-direction: column;

  .editor__table {
    max-width: 100%;
    border: 1px solid black;
    height: 500px;
    overflow-y: scroll;
    scrollbar-width: 0;

    &::-webkit-scrollbar {
      width: 0 !important;
    }
  }

  .editor__insert {
    max-width: 100%;
    padding: 0;
    overflow: scroll;
    margin-top: 16px;

    &::-webkit-scrollbar {
      width: 0 !important;
    }

    input {
      max-width: 60px;
    }

    .editor__insert__table {
      border: 1px solid black;
    }
  }

  .editor__controller {
    width: 100%;
    display: flex;
    justify-content: space-evenly;
  }
}
</style>
