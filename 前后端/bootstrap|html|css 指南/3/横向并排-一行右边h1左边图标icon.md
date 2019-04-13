### 2.4.4 横向并排：h1右边，icon图标左边
因为 h1 字体换行时，即使只有一个字也会占满一行，所以用 『float 或 栅格』都不能实现并排，这时要在 h1 上使用 `display: inline;` 把块元素转为内联元素。	
scss 文件
```
.star {  
  i {  
    font-size: 25px;  
  color: #31dae2;  
  float: left;  
  margin-top: 10px;  
  }  
}
```
html 文件
```
<div class="star">  
  <i class="far fa-bookmark"></i>  
  <h1>再学习6节就可以完成本章了再学习6节就可以完成本</h1>  
</div>
```