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