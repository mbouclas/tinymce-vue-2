# tinymce-vue-2
A vue 2 component for TinyMCE.
# Install
`npm install tinymce-vue-2`

# How to use
* Make sure that window.tinymce is present or it will not work
* Then in your code just import it like so : `import TinyMCE from 'tinymce-vue-2';`
* Finally, added to your component as components. If you want it globally available
you can just to this : `Vue.component('tiny-mce', TinyMCE);`
* Check the [examples](#examples) on how to use it in your template

# Examples
Using the default options, you just need to pass an id and a model
```
<tiny-mce id="description" v-model="description"></tiny-mce>
```

Check the binding by doing something like `<div v-html="description"></div>` anywhere in your
template.

Check bellow on how to configure and extend the editor.

### Changing the menubar
[Read the documentation first](https://www.tinymce.com/docs/configure/editor-appearance/#menubar)

Pass a prop called menubar which is either a string or a string variable. It can either be
a string or a boolean

```
<tiny-mce id="descriptionLong"
        v-model="descriptionLong"
        :toolbar="'undo redo'"
></tiny-mce>
```

### Changing the toolbar
[Read the documentation first](https://www.tinymce.com/docs/configure/editor-appearance/#toolbar)

Pass a prop called toolbar which is either a string or a string variable
to set the toolbar
```
<tiny-mce id="descriptionLong"
        v-model="descriptionLong"
        :toolbar="'undo redo'"
></tiny-mce>
```

It can also be an array which will set multiple toolbars
```
[
    'undo redo | styleselect | bold italic | link image',
    'alignleft aligncenter alignright'
  ]
```

or even a boolean like `false` to disable it

### Passing other configuration options
You can pass any of the documented options to the editor using the otherProps property like so

[Read the documentation first](https://www.tinymce.com/docs/configure/editor-appearance)


```
<tiny-mce id="descriptionLong"
        v-model="descriptionLong"
        :other-props="{min_height:500, elementpath: false, allow_conditional_comments: false}"
></tiny-mce>
```

This allows you to freely configure the editor since all it does is merging your object
with the `tinymce` one