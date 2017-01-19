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
  },
  mounted () {
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
    },
    ...this.otherProps
  })
},
  destroyed () {
    tinymce.get(this.id).destroy();
  }
}
</script>
