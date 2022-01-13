# syno-acme

Update: 
更合理的部署方式参见：
- https://www.bilibili.com/read/cv13914241
- https://github.com/acmesh-official/acme.sh/wiki/Synology-NAS-Guide



---

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

执行脚本

```shell
# 设置 ZeroSSL 账户，参见 https://github.com/acmesh-official/acme.sh/wiki/ZeroSSL.com-CA
export ACME_EAB_KID="xxxx"
export ACME_EAB_HMAC_KEY="xxxx-xxxx"

# 你主域名，如 baidu.com sina.com.cn 等，申请脚本会带上泛域名
export DOMAIN=your_domain

# DNS类型，根据域名服务商而定
export DNS=dns_xxx

# DNS API 生效等待时间 值(单位：秒)
# 某些域名服务商的API生效时间较大，需要将这个值加大(比如900)
export DNS_SLEEP=120

# 阿里云 DNS=dns_ali
export Ali_Key="LTqIA87Kdjevsf5"
export Ali_Secret="0p5EYueFNq51xnxPzKNbx6K51qPH2"

# Dnspod DNS=dns_dp
export DP_Id="1234"
export DP_Key="sADDsdasdgdsf"

# Godaddy DNS=dns_gd
export GD_Key="sdfsdfsdfljlbjkljlkjsdfoiwje"
export GD_Secret="asdfsdfsfsdfsdfdfsdf"

# AWS DNS=dns_aws
export AWS_ACCESS_KEY_ID="sdfsdfsdfljlbjkljlkjsdfoiwje"
export AWS_SECRET_ACCESS_KEY="xxxxxxx"

# Linode DNS=dns_linode
export LINODE_API_KEY="xxxxxxxx"

# 执行脚本
path/cert-up.sh
```

使用阿里云 DNS 举例：

```shell
export ACME_EAB_KID="xxxx"
export ACME_EAB_HMAC_KEY="xxxx-xxxx"
export DOMAIN=your.domain
export DNS=dns_ali
export DNS_SLEEP=120
export Ali_Key="xxxxx"
export Ali_Secret="xxxxx"

path/cert-up.sh
```

原文档如下：

通过acme协议更新群晖HTTPS泛域名证书的自动脚本

使用方法参见: [http://www.up4dev.com/2018/05/29/synology-ssl-wildcard-cert-update/](http://www.up4dev.com/2018/05/29/synology-ssl-wildcard-cert-update/)
