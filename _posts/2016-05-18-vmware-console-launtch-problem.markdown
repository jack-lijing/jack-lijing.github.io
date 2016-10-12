---
layout: post
title:	"vmware vSphere Web Client Connect VM Console Failed reason"
date:	2016-05-19
categories: computer
---
原来一直通过远程登录Windows虚拟机运行vsphere-client管理VMWare平台，由于业务需要，需要采用web形式进行远程管理，其他一切都好，可是当我部署完虚拟机后，需要进入console界面配置IP时，发现虚拟机的console一直显示不出来，在内网访问web端可以，但到了外网就不灵了，通过tcpdump抓包，我发现两个问题

1. 内外网的DNS服务器配置不一致，外网的域名没有指向正确的宿主机地址。这点我通过修改/etc/hosts文件绕过

2. 外网在访问Console过程中需要进行ssl认证，可是此集群中的证书生成是将认证领域限定为 localhost.localdomain，导致外网中浏览器和服务器握手失败，而内网中可成功的情况，需要重新生成证书来解决。
