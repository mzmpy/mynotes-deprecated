<template>
  <div ref="monacoEditor"></div>
</template>

<script>
  import * as monaco from 'monaco-editor';

  export default {
    name: 'MonacoEditor',

    data() {
      return {
        editor: null,
      };
    },

    mounted() {
      this.editor = monaco.editor.create(this.$refs.monacoEditor, {
        value: '',
        theme: 'vs-dark',
        automaticLayout: true,
        language: 'javascript'
      });
    },
  };
</script>

<style>

</style>