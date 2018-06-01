# 任务二. 认识开发工具

## 今天完成的事情

- IDE & 编辑器对比
- 版本管理工具学习
- Git基本操作
- 代码托管平台对比
- 服务器使用学习

## 明天计划的事情

分析任务三, 完成规划及部分开发

## 遇到的问题

暂无

## 收获

1. IDE & 编辑器对比  参考:[Atom、Sublime Text、VSCode 三者比较，各有哪些优势和弱势？](https://www.zhihu.com/question/41857899?sort=created)
  - Webstorm: 一款成熟的IDE，对网站开发者友好，插件齐全功能强大，对于前端开发帮助极大;
  - VisualCode: 
    - 微软开源代码编辑器，可通过安装插件来应用在各种开发场景;
    - Windows & Linux & Mac都有, 界面优雅性能稳定，简单强大的插件系统, Windows上最适用代码编辑器;
    - Terminal 内置!
  - Sublime: 老牌非开源代码编辑器. 功能强大启动速度快,各平台表现都很好, 但是装了插件之后markdown支持也不好（嫌弃脸
  - Atom：开源老牌编辑器，有活跃的开源社区支持,够hack,对电脑顶配的前端开发者友好... 稳定性差，Windows上表现不好

2. 版本管理工具学习
  - 代码版本控制对比 参考：[Git优势](https://www.zhihu.com/question/19601997) & [发展](https://www.zhihu.com/question/25491925)
    - 本地式(第一代):
      - 特点: 实现了基础的代码管理功能, 但是无法协作;
      - 代表: SCCS(1972)、 PVCS(1985)
    - 客户端-服务器式(第二代):
      - 特点：
        - 优点: 实现了**中心服务器端的代码版本管理**, 允许多人对同一个代码库进行同步&修改
        - 缺点:
          1. 断网受限: 断网时无法查看日志, 也无法提交和比较版本;
          2. 分支管理困难: 不支持本地分支, 且创建的分支难以修改;
          3. 中心化: 中心化意味着需要时刻做好灾备, 备份频率需求与较高的备份成本相互掣肘;
          4. 慢: 代码备份&查询&对比都需要与服务器通信, 服务器负载大, 表现出来的结果就是慢;
      - 代表：CVS(1986)、 ClearCase(1992)、Visual SourceSafe(1994)、Perforce(1995)、Subversion(2000,即SVN)
    - 分布式(第三代):
      - 特点:
        - 优点: 结合前两代优点，并且解决了前两代的弊端
          1. 分布式: 断网时可查本地库中的日志, 亦可提交代码、创建分支, 分块管理;
          2. 快：负载分流管理，使用体验为快速;
          3. 社区: Github社区的火爆推动Git的流行;
        - 缺点: 有一定学习曲线, 不过基础使用入门不难;
      - 代表: Git(2005)、Mercurial(2005)
3. Git基本操作 参考: [Git教程-廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001373962845513aefd77a99f4145f0a2c7a7ca057e7570000)
  - 提交操作
    1. 初始化: ```git init```
    2. 全部加入缓存区: ```git add .```
    3. 提交缓存区文件: ```git commit -m "本次提交描述"```
    4. 添加远程库链接: ```git remote add origin <远程库链接>```
    5. 初次推送到添加的远程库: ```git push -u origin master```
    6. 再次推送到添加的远侧库: ```git push origin master```
  - 分支操作
    - 本地：
      1. 查看分支: ```git branch```
      2. 创建分支: ```git branch 新分支名```
      3. 切换分支: ```git checkout 已有分支名```
      4. 删除分支: ```git branch -d 已有分支名```
    - 远程:
      1. 查看分支(带*号为本地分支): ```git branch -a```
      2. 删除远程分支:
      ``` bash
        git branch -r -d 远程分支名
        git push origin :远程分支名
      ``` 
4. 代码托管平台对比
  - [Github](https://github.com/): 世界最大同性交友社区(雾 
    - 优点: 开源项目丰富品种齐全, 适合自己做练手和公开项目用, 支持CI;
    - 缺点: 国内有点慢, 私有仓库要收费, 不支持演示;
  - [码云](https://gitee.com/contrast): 本土化开源社区 参考: [码云评价](https://www.zhihu.com/question/50212423) & [官方对比](https://gitee.com/contrast)
    - 优点: 适合中国国情, 速度快, 有免费私有库用, 支持一键部署到演示平台(有空试试), 支持项目点评, 支持代码质量分析;
    - 缺点: 据说CI支持不够完善, 待验证
  - [Coding](https://coding.net/)
    - 特点: 集成项目管理、集成WebIDE在线开发环境、标准化拓展接口
  - [Gitlab](https://about.gitlab.com/): 公司内部代码管理
    - 特点: 可根据需要整合其他工具, 参考: [gitlab+jira] (https://www.zhihu.com/question/46357590/answer/133005862)
5. 服务器使用学习
  - 购买云服务器: 阿里云、腾讯云
  - 购买之后:
    - 远程登录, 搭建Apache或者Nginx, 然后放置网站在指定路径, 完成外网访问支持;
    - 买域名, 审核后绑定服务器, 完成域名访问支持; 
  - Apache & Nginx 对比 参考:[Nginx和Apache各有什么优缺点](https://www.zhihu.com/question/19571087)
    - Apache:
      - 适合处理动态请求
      - 模块支持好
      - bug少，稳定
      - rewrite功能强大
    - Nginx:
      - 轻量级, 配置简洁, 优势在于处理静态请求
      - 并发支持好,资源使用少
      - 高度模块化设计
      - 社区活跃
    - 结合: 前端用Nginx作为反向代理抗压, apache作为后端处理动态请求
  - Nginx环境搭建(Centos): 参考[How to install and configure NGINX on CentOS7](https://www.godaddy.com/garage/how-to-install-and-configure-nginx-on-centos-7/) 
    - 下载安装: @官网照写
      - 编辑nginx.repo
      - yum install epel-release
      - yum install nginx
    - 状态操作
      - 启动: systemctl start nginx.service
      - 查询: systemctl status nginx.service
      - 停止: systemctl stop nginx.service
    - 开机启动设置: systemctl enable nginx.service 
    - 目录
      - 网站文件默认存放目录：/usr/share/nginx/html
      - 网站默认站点配置：/etc/nginx/conf.d/default.conf
      - 自定义Nginx站点配置文件目录：/etc/nginx/conf.d
      - Nginx全局设置：/etc/nginx/nginx.conf
      - Nginx启动：nginx -c nginx.conf
