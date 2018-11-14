## AJAX实例

先看实例
```html
<html>

<head>
<script>
function loadXMLDoc()
{
var xmlhttp;
if (window.XMLHttpRequest)
  {// code for IE7+, Firefox, Chrome, Opera, Safari
  xmlhttp=new XMLHttpRequest();
  }
else
  {// code for IE6, IE5
  xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
  }
xmlhttp.onreadystatechange=function()
  {
  if (xmlhttp.readyState==4 && xmlhttp.status==200)
    {
    document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
    }
  }
xmlhttp.open("GET","/demo/ajax/ajax_info.txt",true);
xmlhttp.send();
}
</script>

</head><body>
<div id="myDiv"><h2>使用 AJAX 修改该文本内容</h2></div>
<button type="button" onclick="loadXMLDoc()">修改内容</button>
</body>
</html>
```

---

### AJAX实例解析

上面的`AJAX`应用程序包含一个`div`和一个按钮。

`div`部分用于显示来自服务器的信息。当按钮被点击时，它负责调用名为`loadXMLDoc()`的函数：
```html
<!DOCTYPE html>
<html>
<body>

<div id="myDiv"><h2>Let AJAX change this text</h2></div>
<button type="button" onclick="loadXMLDoc()">Change Content</button>

</body>
</html>
```
接下来，在页面的 `head` 部分添加一个 `<script>` 标签。该标签中包含了这个 `loadXMLDoc()` 函数：
```html
<head>
<script>
function loadXMLDoc()
{
.... AJAX script goes here ...
}
</script>
</head>
```
下面的章节会为您讲解 AJAX 的工作原理。