<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png">
        <Editor :value="value"
                :tools="editorTools"
                :content-style="editorStyles"
                ref="editor"
                @change="changeValue" />
    </div>
</template>

<script lang="ts">
import Vue from 'vue';
import { Editor, EditorChangeEvent } from '@progress/kendo-vue-editor';
import '@progress/kendo-theme-bootstrap/dist/all.css';

export default Vue.extend({
  name: 'HomeView',
  components: {
    Editor,
  },
  data() {
    return {
      value: '',
      editorStyles: {},
      editorTools: {},
    };
  },
  created() {
    this.editorStyles = {
        'max-width': '100%',
        'max-height': '500px',
    };

    this.editorTools = [
        'FormatBlock',
        'ForeColor',
        ['Bold', 'Italic', 'Underline'],
        ['AlignLeft', 'AlignCenter', 'AlignRight', 'AlignJustify'],
        ['OrderedList'],
        ['Link', 'Unlink', 'InsertImage'],
    ];
  },
  methods: {
    changeValue(event: EditorChangeEvent) {
        this.value = event.html;
    },
  },
});
</script>
