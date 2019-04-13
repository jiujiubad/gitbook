### 2.4.3 @media 媒体监听
bootstrap 官网：<https://v3.bootcss.com/css/>
1）常用屏幕尺寸
1200px/992px/768px/650px/550px/450px/300px
min-width 填写『常用尺寸』因为刚好不换行，max-width 填写『常用尺寸-1px』		
2）用法
```
.course-img img, .title, .title-cover, .block, a .start{  
  @media (max-width: 750px) and (min-width: 500px) {  
    width: 200px;  
  background-color: #4cae4c;  
  }  
  @media (max-width: 950px) and (min-width: 750px) {  
    width: 250px;  
  background-color: yellow;  
  }  
}
```
或
```
@media (max-width: 750px){
  .course-img img {
    width: 250px;  
  }
}
```