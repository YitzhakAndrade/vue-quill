<template>
  <div ref="editor"></div>
</template>

<script>
import Quill from "quill";

export default {
  props: {
    value: {
      type: String,
      default: ""
    },
    config: {
      type: Object,
      default: () => ({
        modules: {
          toolbar: [
            [{ header: [1, 2, 3, 4, false] }],
            ["bold", "italic", "underline"]
          ]
        },
        theme: "snow",
        formats: ["bold", "underline", "header", "italic"]
      })
    }
  },

  data() {
    return {
      editor: null
    };
  },
  mounted() {
    this.editor = new Quill(this.$refs.editor, this.config);

    this.editor.root.innerHTML = this.value;

    this.editor.on("text-change", () => this.update());
  },

  methods: {
    update() {
      this.$emit(
        "input",
        this.editor.getText() ? this.editor.root.innerHTML : ""
      );
    }
  }
};
</script>
