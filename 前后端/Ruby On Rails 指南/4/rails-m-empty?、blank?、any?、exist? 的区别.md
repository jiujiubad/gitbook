### 4.2.2 empty?、blank?、any?、exist? 的区别
《ruby on rails理解.md》，初探present?和exists?：https://ithelp.ithome.com.tw/articles/10205968
present? 方法等价于 !blank?。利用ActiveRecord初始化物件，效能差。
presence 方法的返回值为调用对象，否则返回 nil。
exist? 效能好，ActiveResource下的方法