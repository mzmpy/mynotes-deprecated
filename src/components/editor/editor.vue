<template>
  <div>
    <div ref="monacoEditor" :style="[innerStyle, { textAlign: 'left', overflow: 'hidden' }]"></div>
  </div>
</template>

<script>
  import * as monaco from 'monaco-editor';

  export default {
    name: 'MonacoEditor',

    emits: ['codeChanged'],

    data() {
      return {
        changed: false,
        innerStyle: {
          width: '100%',
          height: '100%',
        },
        code: '',
      };
    },

    methods: {
      getCode() {
        return this.editor.getValue();
      }
    },

    watch: {
      code(val, oldVal) {
        if(val !== oldVal) {
          this.$emit('codeChanged', val);
        }
      },
    },

    mounted() {
      this.editor = monaco.editor.create(this.$refs.monacoEditor, {
        value: '',
        theme: 'vs-dark',
        automaticLayout: true,
        language: 'maekdown',
      });

      this.editor.onDidChangeModelContent(() => {
        this.code = this.getCode();
      });
    },
  };
</script>

<style>

</style>