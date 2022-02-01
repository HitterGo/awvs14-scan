# 免责声明
本项目仅用于安全自查，请勿利用文章内的相关工具与技术从事非法测试，如因此产生的一切不良后果与本项目无关

## awvs14-scan
修复多个Bug，config增加配置参数
config.ini 请使用编辑器更改，记事本会改会原有格式
针对 AWVS 14版本开发的批量扫描脚本，支持log4j漏洞专项，支持联动xray、burp、w13scan等被动批量扫描，灵活自定义
```
********************************************************************
1 【批量添加url到AWVS扫描器扫描】
2 【一键删除扫描器内所有目标】
3 【对扫描器中已有目标，进行扫描】

请输入数字:1
选择要扫描的类型：
1 【开始 完全扫描】
2 【开始 扫描高风险漏洞】
3 【开始 扫描XSS漏洞】
4 【开始 扫描SQL注入漏洞】
5 【开始 弱口令检测】
6 【开始 Crawl Only,，建议config.ini配置好上级代理地址，联动被动扫描器】
7 【开始 扫描意软件扫描】
8 【仅添加 目标到扫描器，不做任何扫描】
9 【仅扫描】apache-log4j(请需先确保当前版本已支持log4j扫描,awvs 14.6.211220100及以上)
请输入数字:?
```

## 14版本脚本功能  
仅支持AWVS14版本的API接口
* 支持URL批量添加扫描
* 支持批量仅扫描apache-log4j漏洞
* 支持对批量url添加`cooKie`凭证进行爬虫扫描
* 支持对批量url添加1个或多个不同请求头
* 支持配置上级代理地址，能结合被动扫描器进行配置扫描,如：`xray`,`w13scan`,`burp`等扫描器
* 支持一键清空所有任务
* 通过配置`config.ini`文件，支持自定义各种扫描参数，如:爬虫速度，排除路径(不扫描的目录),全局`cookie`,限制为仅包含地址和子目录
* 支持对扫描器内已有目标进行批量扫描，支持自定义扫描类型



## Linux AWVS14 docker安装，本版本较新，能支持log4j版本漏洞
推荐使用docker 
```
安装
docker pull xiaomimi8/awvs14-log4j-2022

启动
docker run -it -d -p 13443:3443 xiaomimi8/awvs14-log4j-2022

用户名：admin@admin.com 密码：Admin123
```

## Windows AWVS v14.6.220117111-完美破解版本 修复扫描失败
```
https://cloud.189.cn/t/j6juMb2mmIre (访问码:9xct)  

```



<!-- 彩蛋

## 性能优化(防止awvs宕机)   
主要防止把宿主机资源占满导致服务不可用
#### CPU限制
如： 假机器只有1核，下面是限制awvs最多使用0.5核，  那么主机最多cpu占用率不会超过50%
按机器实际情况配置
```
docker update --cpus 0.5 --memory-swap -1 awvs容器id
```

#### 内存限制
如： 限制awvs 最多占用0.5G内存
按机器实际情况配置
```
docker update --memory 512m --memory-swap -1 awvs容器id
```

#### 容器自启
主要防止意外情况主机的重启 后awvs不会自启
```
docker update --restart=always awvs容器id 
```
-->
