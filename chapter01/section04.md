## AJAX – 向服务器发送请求

XMLHttpRequest 对象用于和服务器交换数据。

---

### 向服务器发送请求

如需将请求发送到服务器，我们使用 `XMLHttpRequest`对象的`open()`和`send()`方法：
```javascript
xmlhttp.open("GET","ajax_info.txt",true);
xmlhttp.send();
```

|方法|	描述|
|---|---|
|open(method,url,async)	|规定请求的类型、URL 以及是否异步处理请求。method：请求的类型；GET 或 POST;  url：文件在服务器上的位置; async：true（异步）或 false（同步）|
|send(string)|	将请求发送到服务器。string：仅用于 POST 请求|


---

### GET 还是 POST？

与 POST 相比，GET 更简单也更快，并且在大部分情况下都能用。

然而，在以下情况中，请使用 POST 请求：

    + 无法使用缓存文件（更新服务器上的文件或数据库）

    + 向服务器发送大量数据（POST 没有数据量限制）

    + 发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠


---

### GET 请求

一个简单的 GET 请求：
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
xmlhttp.open("GET","/try/ajax/demo_test.php",true);
xmlhttp.send();
}
</script>

</head><body>
<h2>AJAX</h2>
<button type="button" onclick="loadXMLDoc()">Request data</button>
<div id="myDiv"></div>
</body>
</html>
```
在上面的例子中，您可能得到的是缓存的结果。

为了避免这种情况，请向 URL 添加一个唯一的 ID：
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
xmlhttp.open("GET","/try/ajax/demo_get.php?t=" + Math.random(),true);
xmlhttp.send();
}
</script>

</head><body>
<h2>AJAX</h2>
<button type="button" onclick="loadXMLDoc()">请求数据</button>
<p>多点击几次按钮看看时间是否会改变</p>
<div id="myDiv"></div>
</body>
</html>
```

如果您希望通过 GET 方法发送信息，请向 URL 添加信息：
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
xmlhttp.open("GET","/try/ajax/demo_test2.php?fname=Henry&lname=Ford",true);
xmlhttp.send();
}
</script>

</head><body>
<h2>AJAX</h2>
<button type="button" onclick="loadXMLDoc()">请求数据</button>
<div id="myDiv" style="color:red;"></div>
</body>
</html>
```

---

### POST 请求

一个简单 POST 请求：
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
xmlhttp.open("POST","/try/ajax/demo_test_post.php",true);
xmlhttp.send();
}
</script>

</head><body>
<h2>AJAX</h2>
<button type="button" onclick="loadXMLDoc()">Request data</button>
<div id="myDiv"></div>
</body>
</html>
```
如果需要像 HTML 表单那样 POST 数据，请使用 `setRequestHeader()` 来添加 HTTP 头。然后在 `send()` 方法中规定您希望发送的数据：
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
xmlhttp.open("POST","/try/ajax/demo_test_post2.php",true);
xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded");
xmlhttp.send("fname=Henry&lname=Ford");
}
</script>

</head><body>
<h2>AJAX</h2>
<button type="button" onclick="loadXMLDoc()">Request data</button>
<div id="myDiv"></div>
</body>
</html>
```

|方法|	描述|
|---|---|
|setRequestHeader(header,value) |向请求添加 HTTP 头。header: 规定头的名称,value: 规定头的值。|