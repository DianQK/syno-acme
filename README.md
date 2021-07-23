# syno-acme

项目 fork 自 https://github.com/andyzhshg/syno-acme，变动内容如下：

master 分支：

- 适配 DSM 7.0（或者说仅支持 7.0
- 移除了 apache
- master/letsencrypt 分支保持使用 letsencrypt

默认的 main 分支：

- 切换到 ZeroSSL 服务商
- 移除了 config 文件，直接使用 export 配置
- 任务中移除了备份功能（主要是简化逻辑，降低维护成本），可以自行备份相关目录

> 7.0 命令行更新 nginx ssl 证书说明见：[https://v2ex.com/t/790035#r_10729240](https://v2ex.com/t/790035#r_10729240)，感谢 [mao13820](https://v2ex.com/member/mao13820) 的帮助。

原文档如下：

通过acme协议更新群晖HTTPS泛域名证书的自动脚本

使用方法参见: [http://www.up4dev.com/2018/05/29/synology-ssl-wildcard-cert-update/](http://www.up4dev.com/2018/05/29/synology-ssl-wildcard-cert-update/)
