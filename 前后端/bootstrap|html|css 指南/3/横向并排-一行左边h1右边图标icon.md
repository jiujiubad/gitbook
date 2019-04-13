### 2.4.3 横向并排：h1左边，icon图标右边
因为 h1 字体换行时，即使只有一个字也会占满一行，所以用 『float 或 栅格』都不能实现并排，这时要在 h1 上使用 `display: inline;` 把块元素转为内联元素。	
scss 文件
```
.title {  
  margin: 50px auto 35px; //因为h1用了display: inline，无法改变margin，所以在这个位置改  
  h1 {  
    display: inline; //让h1和icon图标并排（所以margin、padding属性会因此失效）  
  }  
  i {  
    @media(min-width: 700px){  
      float: right;  
  margin-top: 8px;  
  }  
    font-size: 25px;  
  color: #31dae2;  
  }  
}
```
html 文件
```
<div class="title">  
  <h1>再学习6节就可以完成本章再学习6节就dfas了</h1>  
  <i class="far fa-bookmark"></i>  
</div>
```