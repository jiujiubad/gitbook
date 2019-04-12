# 《ROR 指南》第 3 章 ror gem 常用
## 3.1 调试
### 3.1.1 byebug
1）打开 `/config/puma.rb`
```
# 设置 puma 超时时间（过多少时间推出 byebug）
worker_timeout 5000
```
2）常用
```
<%= debug(params) if Rails.env.development? %>
<%= debug(session[:camp_id]) if Rails.env.development? %>
<%= debug(@current_camp.try(:name)) if Rails.env.development? %>
<%= debug(params[:controller]) if Rails.env.development? %>
<%= debug(request.path) if Rails.env.development? %>
```
### 3.1.2 pry
## 3.2 权限管理
### 3.2.1 devise
### 3.2.2 cancancan
## 3.3 美观
### 3.3.1 bootstrap
### 3.3.2 jquery


## 开发必备的 gem
《算法》《设计模式》《重构改善既有代码的设计》

安装 figaro
```
gem 'pry-rails', '~> 0.3.9', group: :development
gem 'figaro', '~> 1.1', '>= 1.1.1', group: :development
```

pry-rails
pry
pry-byebug + awesome_rails_console 高亮样式

rubocop
overcommit

## 3.4 Markdown 功能
【精】Markdown功能+Pygments-高亮：<http://railscasts.com/episodes/207-syntax-highlighting-revised?view=asciicast>		
Markdown-Pygments-Css样式：<https://github.com/richleland/pygments-css>		
【精】Markdown-Coderay-高亮：<https://ruby-china.org/topics/474>		
Markdown-Coderay-代码块标题code_header：<https://github.com/ryanb/railscasts/blob/master/lib/code_formatter.rb>		
Markdown-coderay-css样式1：<http://railscasts.com/episodes/207-syntax-highlighting?view=asciicast>		
Markdown-Coderay-Css样式2：<http://www.crashingchandelier.com/articles/6-rails-5-blog-with-coderay-syntax-highlighter>	

### 3.4.1 工具对比
0）redcarpet 必备的 Markdown to html 解析器：下载 27150000，最后更新 2016
1）Coderay 推荐第一选择（速度最快，RailsCast 网站使用有 css，但支持语言少）：下载 104,000,000，最后更新 2017
2）pygments.rb 推荐第二选择（支持语言多，Github 网站使用，css 下载 https://github.com/richleland/pygments-css/blob/master/default.css）：下载 3,700,000，最后更新 2017
3）rouge 可用： 是简化的 pygments，下载 19,890,000，最后更新 2018
4）uv 弃用（使用人数太少）：下载 14,000，最后更新 2011
5）kramdown 弃用（适用于 ruby，不适合 rails）：下载 22,420,000，最后更新 2019
6）kramdown-rails 弃用（使用人数太少）：下载 14,000，最后更新 2014

### 3.4.2 推荐1 Coderay
app/helper/application_helper.rb
```
# Markdown 语法高亮：Coderay  
class HTMLwithCodeRay < Redcarpet::Render::HTML  
  def block_code(code, language)  
    if language  
      <<-EOS  
        <div class="code_block"> 
          <div class="code_header"> 
            #{CGI.escapeHTML(language.to_s)}  
          </div> 
          #{CodeRay.scan(code, language ||= :text).div(tab_width: 2, line_numbers: :inline)}  
        </div> 
      EOS  
    else  
      CodeRay.scan(code, language ||= :text).div(tab_width: 2, line_numbers: :inline)  
    end  
  end
end  
# Markdown to Html 解析：Coderay  
def markdown(text)  
  renderer = HTMLwithCodeRay.new(hard_wrap: true, filter_html: true)  
  options = {  
    autolink: true,  
  no_intra_emphasis: true,  
  fenced_code_blocks: true,  
  lax_html_blocks: true,  
  strikethrough: true,  
  superscript: true  
  }  
  Redcarpet::Markdown.new(renderer, options).render(text).html_safe  
end
```
app/assets/stylesheets/coderay.css.scss
```
.CodeRay, .CodeRay pre {  
  font-family: 'Menlo', 'Courier New', 'Terminal', monospace;  
  background-color: #232323;  
  color: #E6E0DB;  
}  
.CodeRay pre {  
  margin: 0px;  
  padding: 0px;  
}  
/*** CODE BLOCKS ***/  
.code_block {  
  margin: 12px 0;  
}  
.code_header {  
  position: relative;  
  background-color: #E0E0E0;  
  font-size: 12px;  
  padding: 4px 7px;  
  border: solid 1px #B6B6B6;  
  border-bottom: none;  
}  
.code_header .clippy {  
  position: absolute;  
  top: 4px;  
  right: 7px;  
}  
.clippy_label {  
  position: absolute;  
  right: 20px;  
  top: 1px;  
  text-align: right;  
  width: 200px;  
  font-size: 10px;  
  color: #555;  
}  
.CodeRay {  
  overflow: auto;  
  border: 1px solid #777;  
  border-top: none;  
  padding: 5px 7px;  
  font-size: 13px;  
  margin: 0;  
  line-height: 17px;  
}  
code {  
  border: solid 1px #CCC;  
  background-color: #EEE;  
  font-family: 'Menlo', 'Courier New', 'Terminal', monospace;  
  padding: 0 3px;  
}  
pre code {  
  display: block;  
  background-color: #EEE;  
  padding: 5px 7px;  
}  
  
.CodeRay .an { color:#E7BE69 }                      /* html attribute */  
.CodeRay .c { color:#BC9358; font-style: italic; } /* comment */  
.CodeRay .ch { color:#509E4F }                      /* escaped character */  
.CodeRay .cl { color:#FFF }                         /* class */  
.CodeRay .co { color:#FFF }                         /* constant */  
.CodeRay .fl { color:#A4C260 }                      /* float */  
.CodeRay .fu { color:#FFC56D }                      /* function */  
.CodeRay .gv { color:#D0CFFE }                      /* global variable */  
.CodeRay .i { color:#A4C260 }                      /* integer */  
.CodeRay .il { background:#151515 }                 /* inline code */  
.CodeRay .iv { color:#D0CFFE }                      /* instance variable */  
.CodeRay .pp { color:#E7BE69 }                      /* doctype */  
.CodeRay .r { color:#CB7832 }                      /* keyword */  
.CodeRay .kw { color:#CB7832 }                      /* keyword */  
.CodeRay .rx { color:#A4C260 }                      /* regex */  
.CodeRay .s { color:#A4C260 }                      /* string */  
.CodeRay .sy { color:#6C9CBD }                      /* symbol */  
.CodeRay .ta { color:#E7BE69 }                      /* html tag */  
.CodeRay .pc { color:#6C9CBD }                      /* boolean */
```
html
```
<%=  markdown  @artical.description  %>
```
### 3.4.2 推荐2 Pygments.rb
app/helper/application_helper.rb
```
# Markdown 语法高亮：Pygment  
class HTMLwithPygments < Redcarpet::Render::HTML  
  def block_code(code, language)  
    Pygments.highlight(code, lexer: language, options: {linenos: true, :full => true})  
  end  
end  
# Markdown to Html 解析：Pygment  
def markdown(text)  
  renderer = HTMLwithPygments.new(hard_wrap: true, filter_html: true)  
  options = {  
    autolink: true,  
  no_intra_emphasis: true,  
  fenced_code_blocks: true,  
  lax_html_blocks: true,  
  strikethrough: true,  
  superscript: true  
  }  
  Redcarpet::Markdown.new(renderer, options).render(text).html_safe  
end
```
app/assets/stylesheets/pygments.css.erb
```
/*控制台输入 Pygments.styles 可以查看所有代码块高亮样式：  
["manni", "igor", "lovelace", "xcode", "vim", "autumn", "abap", "vs", "rrt", "native", "perldoc", "borland", "arduino", "tango", "emacs", "friendly", "monokai", "paraiso-dark", "colorful", "murphy", "bw", "pastie", "rainbow_dash", "algol_nu", "paraiso-light", "trac", "default", "algol", "fruity"]  
*/  
<%=  Pygments.css(style: "default") %>
```
html
```
<%=  markdown  @artical.description  %>
```
