---
layout: post
title:  "自动重置网易企业邮箱员工密码"
date:   2016-10-11 10:42:34 +0800
categories: tools
---
网易企业邮箱启用了新的密码规则，老师不适应这个密码复杂度，经常因为忘记而打电话要求重置，网易邮箱管理端并没有提供默认的重置按钮，我利用Greasemonkey插件编写脚本实现了此功能。

{% highlight javascript %}
// ==UserScript==
// @name        mail.****.*.cn
// @namespace   mail*****.******.*.cn
// @include     https://mailhz.qiye.163.com/domain/*
// @version     1
// @grant       none
// ==/UserScript==

var u = window.location.pathname;

if ( u == '/domain/main'){ 
  window.location.href="https://mailhz.qiye.163.com/domain/ftl/account";
  document.getElementsByTagName('html')[0].style.overflow='visible';
}else if( u == '/domain/ftl/editAccount' ||  u == '/domain/ftl/createAccount' ){
  console.info(u);
  document.getElementsByTagName('html')[0].style.overflow='visible';
  document.getElementsByName('password')[0].value='123456';
  document.getElementsByName('pass_re')[0].value='123456';
}
  
{% endhighlight %}

