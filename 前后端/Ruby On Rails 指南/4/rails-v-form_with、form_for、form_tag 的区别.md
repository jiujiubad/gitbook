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