# Gitbook and my ebooks
第一部分介绍 Gitbook 的使用，以及用脚本部署到 Github-Pages；第二部分是用过的技术栈所要整理出来的 ebooks 电子书。

## Gitbook 教程
【精】2019-03-14 如何优雅地使用Gitbook：<https://cloud.tencent.com/developer/article/1404934>
【精】GitBook 使用教程：<http://gitbook.zhangjikai.com/>

### gitbook 插件  
常用插件如下：  
* "splitter"：左侧目录宽度可以鼠标拖动（中间位置的三个点）调整
* "copy-code-button"：为代码块添加复制的按钮
* "-lunr", "-search", "search-plus"：中文搜索, 需要将默认的 search 和 lunr 插件去掉
* "expandable-chapters-small"：使左侧目录可以折叠
* "anchor-navigation-ex"：添加Toc到侧边悬浮导航以及回到顶部按钮
* "github-buttons"：添加项目在 github 上的 star，watch，fork情况

`touch book.json` 新建文件并填写
```
{
  "title": "Gitbook Use",
  "author": "chu",
  "language": "zh-hans",
  "links": {
    "sidebar": {
      "Home": "https://xiaochu.cf"
    }
  },
  "plugins": [
    "splitter",
    "copy-code-button",
    "-lunr", "-search", "search-plus",
    "expandable-chapters-small",
    "anchor-navigation-ex",
    "github-buttons"
  ],
  "pluginsConfig": {
    "github-buttons": {
      "buttons": [{
        "user": "jiujiubad",
        "repo": "gitbook",
        "type": ["star"],
        "size": "small",
        "count": true
        }
      ]
    }
  }
}
```
### gitbook 用脚本部署到 github-pages
gitbook 常用命令
```
npm install gitbook-cli -g #安装gitbook管理工具
gitbook --version          #查看gitbook版本
gitbook install            #安装插件
gitbook build              #生成html页面
gitbook serve              #生成html页面并开启服务，监听4000端口
```
创建 gh-pages 分支，并在 github 的 Setting-Github Pages 选项中添加该分支
```
git checkout -b gh-pages
```
`touch deploy.sh` 新建脚本并填写
```
#!/bin/bash
# 设置远程仓库的地址
remote_url=git@github.com:jiujiubad/gitbook-test.git
# 获取当前时间
cur_date="`date +%Y-%m-%d-%H:%M:%S`" 
# 生成_book文件
gitbook build

rm -rf .deploy_git/* | egrep .deploy_git/.git
if [ ! -d ".deploy_git/" ];then
 cp -R _book/ .deploy_git/
else
 cp -R _book/* .deploy_git/
fi
cd .deploy_git/
git init
git remote add origin $remote_url
git checkout -b gh-pages
git add -A
git commit -m $cur_date
git push -f origin gh-pages
```
给脚本授权，并执行脚本
```
chmod a+x ./deploy.sh
./deploy.sh
```
部署完成！！打开页面 https://github名称.github.io/仓库名称 查看电子书

## 前后端 ebooks
* 《ROR指南》
* 《Yaml指南》
* 《html和css指南》
* 《微信小程序指南》
* 《Jquery|JavaScript|Ajax指南》
* 《TypeScript指南》
* 《Vue指南》
* 《Flutter指南》

## 工具 ebooks
* 《终端Shell指南》：oh-my-zsh，vim
* 《自搭建指南》：博客，科学上网，私有云盘，下载上传，云播放，ftp服务器
* 《Markdown指南》
* 《Sys-Mac指南》
* 《Sys-Windows指南》
* 《Sys-Linux指南》
* 《虚拟机指南》
* 《电商Solidus指南》
* 《设计与剪辑指南》

## 运维 ebooks
* 《Git指南》
* 《环境-Linux|Ansible指南》
* 《任务-Sidekiq|Sidetiq|Crontab指南》
* 《集群-Docker|Kubernetes|Vagrant指南》
* 《代理-Nginx|Apache指南》
* 《安全-通讯协议|Oauth指南》
* 《数据-Mysql|Postgresql|Redis指南》
* 《自动化测试-Selenium|Appium指南》

## 项目 ebooks
* 《初的文档》
* 《PJ项目》
* 《项目方法论》敏捷过程、Growth Hack、User Story、项目管理