## modal
使用<code>remote</code>加载要展示的内容时，我们也许需要动态设置模态框的标题，正好 Bootstrap 的模态框类提供了一些这样的事件可以供我们使用。也许，我们会这样使用
```code
$("#exampleModal").on('shown.bs.modal', function() {
    $(this).find(".modal-title").html('这是标题');
});
```
但是，有时可能并不成功（为什么是有时？），因为你使用的是<code>remote</code>加载，很可能在代码走到这一步的时候还没有将页面内容加载进来。
所以，我们的处理是使用<code>loaded.bs.modal</code>事件
```code
$("#exampleModal").on('shown.bs.modal', function() {
    $(this).on('loaded.bs.modal', function(event) {
        $(this).find(".modal-title").html('新的标题');
    });
});
```
