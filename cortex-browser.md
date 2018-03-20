# Cortex Browser

- [Introduction](#introduction)
- [Basic Setup](#basic-setup)
- [Available Options](#basic-setup)
- [Window Mode](#window-mode)
- [iFrame Mode](#iframe-mode)

<a name="introduction"></a>
## Introduction

Cortex Browser is a standalone Javascript library, so it does not depend on jQuery or any other library, but comes with support for jQuery.

<a name="basic-setup"></a>
## Basic Setup

First include the library script.

```html
@include('cortex::integrations.browser')
```

The following code is an example for an input and a button element:

```html
<div class="input-group">
  <input class="form-control" id="url">
  <div class="input-group-btn">
    <button type="button" class="btn btn-primary" id="trigger">
      Choose File
    </button>
  </div>
</div>
```

```javascript
var urlInput = document.querySelector('#url');
var trigger = document.querySelector('#trigger');
trigger.addEventListener('click', function(){
  var browser = new CortexBrowser({
    type: 'window',
    onFileSelected: function(url){
      urlInput.value = url;
    }
  });
});
```

<a name="available-options"></a>
## Available Options

<table width="100%">
  <thead>
    <tr>
      <th>Property</th>
      <th>Description</th>
      <th>Type</th>
      <th>Required</th>
      <th>Default</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>type</td>
      <td>"window" or "iframe"</td>
      <td>String</td>
      <td>No</td>
      <td>"window"</td>
    </tr>
    <tr>
      <td>mode</td>
      <td>URL param mode defined in your cortex.php</td>
      <td>String</td>
      <td>No</td>
      <td>"popup"</td>
    </tr>
    <tr>
      <td>initialFolder</td>
      <td>Initial folder path</td>
      <td>String</td>
      <td>No</td>
      <td>"/"</td>
    </tr>
    <tr>
      <td>iframe</td>
      <td>If you are using "iframe" mode, you must specify either a iframe element, a query selector string or a jQuery collection.</td>
      <td>HTMLIFrameElement|String|jQuery</td>
      <td>Yes (if type is "iframe")</td>
      <td>undefined</td>
    </tr>
    <tr>
      <td>onFileSelected</td>
      <td>A callback function which is executed after a file is selected. A url parameter is passed to this function.</td>
      <td>Function</td>
      <td>No</td>
      <td>undefined</td>
    </tr>
    <tr>
      <td>onClosed</td>
      <td>A callback function when a window is closed.</td>
      <td>Function</td>
      <td>No</td>
      <td>undefined</td>
    </tr>
  </tbody>
</table>

<a name="iframe-mode"></a>
## iFrame Mode

A more convinient way to call Cortex is with an iFrame element, so there are no pop-up windows.

Here is an example on how you can call Cortex with an iFrame that is in a bootstrap modal dialog:

```html
<div class="modal fade" tabindex="-1" role="dialog" id="iframe-modal">
  <div class="modal-dialog modal-lg" role="document">
    <div class="modal-content">
      <div class="modal-body">
        <iframe id="iframe-window" src="#" style="width:100%;height: 400px;border:0;"></iframe>
      </div>
    </div>
  </div>
</div>
```

```javascript
$(document).on('click', '#trigger', function(){
  $('#iframe-modal').modal('show');
  var browser = new CortexBrowser({
    type: 'iframe',
    iframe: $('#iframe-window'),
    onFileSelected: function(url){
      $('#url').val(url);
      $('#iframe-modal').modal('hide');
    }
  });
});
```