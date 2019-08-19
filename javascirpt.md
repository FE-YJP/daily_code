### js读取文件、图片

#### html

```
<input type="file" onchange="previewFile()"><br>
<img src="" height="200" alt="Image preview...">
```

#### javascript

```
javascript
function previewFile() {
  var preview = document.querySelector('img');
  var file    = document.querySelector('input[type=file]').files[0];
  var reader  = new FileReader();

  reader.addEventListener("load", function () {
    preview.src = reader.result;
  }, false);

  if (file) {
    reader.readAsDataURL(file);
  }
}
```

