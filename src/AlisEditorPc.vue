<template lang="html">
  <div id="ALISEditor">
    <div class="container" id="editor"></div>
  </div>
</template>

<script>
import Vue from 'vue'
import BalloonEditor from '@ckeditor/ckeditor5-editor-balloon/src/ballooneditor'
import BoldPlugin from '@ckeditor/ckeditor5-basic-styles/src/bold'
import ItalicPlugin from '@ckeditor/ckeditor5-basic-styles/src/italic'
import LinkPlugin from '@ckeditor/ckeditor5-link/src/link'
import Paragraph from '@ckeditor/ckeditor5-paragraph/src/paragraph'
import ParagraphButtonUI from '@ckeditor/ckeditor5-paragraph/src/paragraphbuttonui'
import Heading from '@ckeditor/ckeditor5-heading/src/heading'
import HeadingButtonsUI from '@ckeditor/ckeditor5-heading/src/headingbuttonsui'
import BlockQuote from '@ckeditor/ckeditor5-block-quote/src/blockquote'
import EssentialsPlugin from '@ckeditor/ckeditor5-essentials/src/essentials'

export default Vue.extend({
  data() {
    return {
      editor: null
    }
  },
  mounted() {
    BalloonEditor.create(document.querySelector('#editor'), {
      plugins: [
        EssentialsPlugin,
        BoldPlugin,
        ItalicPlugin,
        LinkPlugin,
        Heading,
        HeadingButtonsUI,
        ParagraphButtonUI,
        Paragraph,
        BlockQuote
      ],
      toolbar: ['bold', 'italic', 'link', 'heading1', 'heading2', 'paragraph', 'blockQuote'],
      heading: {
        options: [
          { model: 'paragraph', title: 'Paragraph', class: 'ck-heading_paragraph' },
          { model: 'heading1', view: 'h1', title: 'Heading 1', class: 'ck-heading_heading1' },
          { model: 'heading2', view: 'h2', title: 'Heading 2', class: 'ck-heading_heading2' }
        ]
      }
    }).then((editor) => {
      this.editor = editor
    })
  }
})
</script>

<style lang="scss">
.container {
  width: 640px;
  margin: 10px auto;
  font-size: 16px;
}
</style>