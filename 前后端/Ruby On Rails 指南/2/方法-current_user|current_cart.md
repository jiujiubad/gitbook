## 1.10 定义 current_user、current_cart、current_xxx
修改 xxx_helper.rb
```
def current_camp
  @current_camp ||= find_camp
end

def find_camp
  if (camp_id = params[:camp_id])
    session[:camp_id] = camp_id
    Camp.find_by(id: camp_id)
  elsif camp_id.blank? && session[:camp_id]
    Camp.find_by(id: session[:camp_id])
  else
    Camp.first
  end
end
```
修改 app/controllers/application_controller.rb
```
include XxxHelper
```