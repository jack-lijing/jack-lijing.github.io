---
layout: post
title:	"快速连接交换机"
date:	2016-10-10
categories:	network
---
linux天生的网络基因，加点代码就可以用键盘快捷远程控制路由器，我每次都敲的很爽。

* /*etc/hosts 增加路由器域名映射
* ~/.bashrc 添加alias别名
* 编写脚本，用expect实现密码的自动化

{% highlight shell %}

#!/usr/bin/expect
set ip [lindex $argv 0]
spawn ssh $ip
expect "*password:"
send "***************************\r"
expect "*>"
interact
{% endhighlight %}
