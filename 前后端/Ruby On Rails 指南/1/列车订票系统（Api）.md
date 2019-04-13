## 2.7 列车订票系统（Api）
@data7 Web API 实作 3-1 to 7-7: <https://xiaochu.ga/Content/syllabus_dsrUtj.html>
@data7 Rails 自动化测试 5-1 to 5-9: <https://xiaochu.ga/Content/syllabus_wzHTVX.html>
### 2.7.1 需求
* 可以查询有哪些列车
* 可以查询特定列车有哪些空位
* 可以订票，并得到一组订票号码(乱数产生)
* 根据订票号码，可以查询订票资料
* 根据订票号码，可以修改订票资料
* 根据订票号码，可以取消订票

* 使用者可以在网页上注册、登入，拿到 API Key
* 如果在有登入的情况下进行订票的话，则可以查询该用户下的所有订票
* 注册、登入和登出的 API，好让用户输入帐号密码登入，拿到 API Key
* 更新自己的资料，包括修改 E-mail、密码和上传照片
* 查询自己的资料
* GET 拿资料可能会很复杂，因为资料字段很多，使用 JBuilder 来定义 JSON

* 测试注册 API:
* 测试登入登出 API
* 测试查询列车 API
* 测试查询订票、修改定票、取消订票 API
* 测试订票 API
* 测试查询我全部的订单 API
* 测试查询和更新我的资料 API