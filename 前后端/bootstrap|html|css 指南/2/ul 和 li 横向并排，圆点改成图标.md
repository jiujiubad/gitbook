### 2.4.2 ul 和 li 横向并排，圆点改成图标
* bootstrap 方式
```
<ul class="list-unstyled">  <!--去除圆点-->
<ul class="list-inline">    <!--横向并排-->
```
* css 方式
```
ul {  
  list-style: none;  //去除圆点
}
li a:before {  
  display:inline;    //横向并排
  content: "\f101";  //圆点前加入图标
  color: #fff;  
  font-family: 'FontAwesome';  
  margin-right: 10px;  
}
```