### 2.4.8 fontawesome doesn't work 显示为正方形：换用新版本
Gemfile
```
# 弃用 gem 'font-awesome-rails', '~> 4.7'
# 前端图标icon
gem 'font-awesome-sass', '~> 5.8'
```
application.html.rb
```
<link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.2.0/css/font-awesome.min.css" rel="stylesheet">
```