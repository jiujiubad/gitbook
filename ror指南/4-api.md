# 《ROR 指南》第 4 章 ror api
## 4.1 RailsApi Routes

## 4.2 RailsApi Model
### 4.2.1 destroy 和 delete_all 的区别
？delete 是数据库级别的？
### 4.2.2 empty?、blank?、any?、exist? 的区别
《ruby on rails理解.md》，初探present?和exists?：https://ithelp.ithome.com.tw/articles/10205968
present? 方法等价于 !blank?。利用ActiveRecord初始化物件，效能差。
presence 方法的返回值为调用对象，否则返回 nil。
exist? 效能好，ActiveResource下的方法

## 4.3 RailsApi Controller
### 4.3.1 build 和 new 的区别
？new 用于新建表单，build 用于新建对象？
### 4.3.2 filter(params)
编译过滤器

## 4.4 RailsApi View
### 1.4.1 form_with、form_for、form_tag 的区别
官网：https://ruby-china.github.io/rails-guides/5_1_release_notes.html
Rails 5.1 之后，把后两个统一为 form_with
```
# 只使用 URL
<%= form_with url: posts_path do |form| %>
# 指定作用域，添加到输入字段的名称前
<%= form_with scope: :post, url: posts_path do |form| %>
# 使用模型，从中推知 URL 和作用域
<%= form_with model: Post.new do |form| %>
# 现有模型的更新表单填有字段的值：
<%= form_with model: Post.first do |form| %>
```
form_with 的设置默认 `remote:true`，不想用 remote 就需要手动设置 `local: true`
Ruby-China-Jasl：「Rails5 推荐 form_with 然后不提供 `local:true` 来实现『Ajax 模式』提交」

## 4.5 RubyApi
### 4.5.1 数组
uniq 去重
compact 去所有 nil   
### 4.5.2 字符串
chomp 去最后一个换行符
strip 去开头结尾的空格
