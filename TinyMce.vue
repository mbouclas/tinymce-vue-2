<template>
    <div>
      <textarea :id="id" :value="value"></textarea>
    </div>
</template>

<script>
export default {
  name : 'tiny-mce',
  props : {
     id: {
        type: String,
        default: 'editor'
      },
      value: {
        type: String,
        default : ''
      },
      toolbar: {
        default: ''
      },
      menubar: {
        default: ''
      },
      otherProps: {
        default: ''
      },
      baseURL: {
        type: String,
        default: ''
      },
  },
  mounted () {
  tinymce.baseURL = this.baseURL;
  tinymce.init({
    selector: `#${this.id}`,
    toolbar : this.toolbar,
    menubar : this.menubar,
    init_instance_callback: (editor) => {
      editor.on('KeyUp', (e) => {
        this.$emit('input', editor.getContent());
      });

      editor.on('Change', (e) => {
        this.$emit('input', editor.getContent());
      });
      
      editor.setContent(this.value);
    },
    ...this.otherProps
  })
},
  destroyed () {
    tinymce.get(this.id).destroy();
  }
}
</script>
