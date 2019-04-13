### 2.1.2 鼠标悬停显示遮罩层-jquery 方式
![](https://ws1.sinaimg.cn/large/006tKfTcgy1g1puggdvh5g30ap07mwiz.gif)	
scss 文件
```
/*  
1.position（最外层盒子用 relative，内层盒子都用 absolute）、z-index、top 定位，让盒子重叠  
2.width、height 定形，让大小重叠
3.display: none 隐藏盒子，jquery 的 mouseover 鼠标悬停显示盒子，jquery 的 mouseout 鼠标离开隐藏盒子  
*/  
.my_box {  
  /*外层相对位置：为了让盒子位置重叠*/  
  position: relative;  
  /*宽高：撑开鼠标悬停前的盒子*/  
  img {  
    /*定位*/ 
  position: absolute;
  z-index: 1; 
    /*定形：撑开鼠标悬停前的盒子*/  
  width: 400px;  
  height: 280px;  
  }  
  a {  
    .mask {  
      /*里层绝对位置：为了让盒子位置重叠*/  
  position: absolute; 
  z-index: 2; 
  top: 0;   
  /*宽高：撑开鼠标悬停后的盒子*/  
  width: 400px;  
  height: 280px;  
  /*样式：鼠标悬停前*/  
  display: none; /*隐藏，属性解说：http://www.runoob.com/cssref/pr-class-display.html*/  
  background: rgba(101, 101, 101, 0.6);  
  color: #fff;  
  text-align: center;  
  padding-top: 80px;  
  }  
  }  
}
```
html 文件
```
<div class="my_box">  
  <%=  image_tag("https://ws3.sinaimg.cn/large/006tNbRwgy1fvziqfqj28j30et08c74m.jpg") %>  
  <a href="#">  
    <div class="mask">  
      <h3>A Picture of food</h3>  
      <button type="button" class="btn btn-success">成功按钮</button>  
    </div>  
  </a>  
</div>
```
js 文件
```
$(function () {  
  $(".my_box").mouseover(function () {  
    $(".mask").show();  
  });  
  $(".my_box").mouseout(function () {  
    $(".mask").hide();  
  });  
});
```