---
title: "pg中对中文字段的排序"
tags: ['database']
categories: ['database']
---
<!-- gb18030 -->
PostgreSQL中对字段排序时中文并不会按照拼音排序，在不同的字符集中，汉字的编码可能不一样，比如UTF8和GBK，其中GBK大致是按拼音的顺序进行编码的，而UTF8则不是。所以如果你的数据库使用了UTF8编码，对中文字段进行排序时，得到的并不是按拼音排序的结果。
PostgreSQL中，中文按拼音排序的编码包括GB18030, EUC_CN, GBK, BIG5, EUC_TW 等。为了得到拼音排序，可以使用编码转换后的值来排序，如`convert_to(name,'GBK')`。

>对于多音字、生僻字排序结果不太准确：如根据[汉字内码扩展规范(GBK)](http://ff.163.com/newflyff/gbk-list/) 在GBK编码10进制`濮`编码为58791，`总`编码为55260,

