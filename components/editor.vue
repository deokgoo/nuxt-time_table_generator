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
        <small id="titleHelp" class="form-text text-muted">We'll never share your title with anyone else.</small>
      </div>
    </form>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

type Status = {
  editTitle: String
}

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
}
</style>
