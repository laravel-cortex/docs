# Integration

- [TinyMCE](#tinymce)
- [CKEditor](#ckeditor)
- [Custom](#custom)

Cortex comes with several integrations out of the box!

<a name="tinymce"></a>
## TinyMce

For a basic out of the box setup, include the integration script after TinyMCE, like this:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/tinymce/4.7.9/tinymce.min.js"></script>
@include('cortex::integrations.tinymce-config')
```

This will setup your TinyMCE to use Cortex in popup mode as its file browser.

<a name="ckeditor"></a>
## CKEditor

For a basic out of the box setup, include the integration script after CKEditor, like this:

```html
<script src="//cdnjs.cloudflare.com/ajax/libs/ckeditor/4.5.11/ckeditor.js"></script>
<script src="//cdnjs.cloudflare.com/ajax/libs/ckeditor/4.5.11/adapters/jquery.js"></script>
@include('cortex::integrations.ckeditor-config')
```

As CKEditor requires an external script for its configuration, you can change the configuration in ```ckeditor-config.js``` which will be loaded from the assets path defined in the ```cortex.php``` configuration file.

<a name="custom"></a>
## Custom

Cortex ships with a little Javascript library called Cortex Browser. It's a standalone library, so it does not depend on jQuery or any other library, but comes with support for jQuery.

Head over to [Cortex Browser](cortex-browser.md) page to learn more.