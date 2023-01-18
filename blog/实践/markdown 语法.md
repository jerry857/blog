## 标题
格式语法前+ space 空格  
\# 一级标题  
\#\# 二级标题  
\#\#\# 三级标题  
## 段落
### 首行缩进
不用想着首行缩进，新起一行即可
要不然就是  
  在中文模式下两个space或者
 &#160; &#160; &#160;来实现缩进
### 换行 
在一行的末尾添加两个或以上空格+回车
或者结尾使用使用 \<\b\r\>
### 粗体bold
加粗文字前后各添加两个**星号** \*\* ，或者__下划线__
推荐使用星号\*\*，因为有些不兼容
### 斜体ltalic
*一个*星号\*.
### ltalic & bold
***三个星号*** \*\*\*，前后各添加三个
### 引用
> 这就是引用， 段落前加\>
> 还可以包含多个段落，只需要加一个>的空白行即可
> 但这个渲染用不到就是了
>> 还可以嵌套
>> 使用方法是前面加两个 \>\>
>> 还可以 *这样*
>> *这样*
>> 不过需要先调试一下
### 列表
#### 有序列表
1. 基本上就是开头是\1\.
2. 剩下的数字也随意
	1. 也可以加tab键，会有惊喜
#### 无序列表
 * 就是前面加一个\*，即可，别添加两个
 * 或者添加 \- 或者 \+ 
 * 尽量统一，要不然也挺乱的
	 * 还可以试一下制表符tab
	 * 或者引用块	
* 这样
	>这样，不过说实话，有点难看
- 不过也问题不大
### 代码块
代码块用四个空格或者一个制表符
	这样子
	1. open visual studio
		或者这样
### 图片
![头像.jpg](https://gitee.com/jerry-857/images/raw/master/photo_2023-01-12_22-48-30.jpg)
\!\[photo_2023-01-12_22-48-30.jpg]\(https://gitee.com/jerry-857/images/raw/master/photo_2023-01-12_22-48-30.jpg)
这个是图床语法
如果是使用本地，也是一样。只不过是链接改为(\/user\/local)
这些列表都可以随意组合
## 代码
如果将单词或短语改为代码，可以给包裹在反引号\` \` 之内，例如 `这样` 
``如果是整段代码`并且`包含小代码，可以这样用``
如果是代码块
	用制表符即可
	tab
如果不想缩进的
```
三个反引号即可
```
语法高亮
```json
{
"firstname": "john",
"lastname": "smith",
"age":25
}
```
## 分割线
单独一行上使用
***
三个或者多个\*\*\*，或者下划线
___
或者破折号
\-\-\-

---

不过使用破折号的时候前后均需要添加空白行

## 链接语法

markdown 语法
\[超链接显示名\](超链接地址 "超链接title")
so，例如
这是一个超链接[markdown语法](https://markdown.com.cn "markdown")
链接title，这玩意儿又称为隐信息，切记有空格，不然就附加信息了
###  输入网址
<https://markdown.com.cn>
或者邮箱
<mirrorcloud3@gamil.com>
用 \<\> 尖括号完成
顺便可以和粗体或者斜体组合使用
**[52](https://52pojie.cn “吾爱论坛”)**
*[chaoxing](https://www.chaoixng.com "学习通")*
### 引用类型链接
怎么说呢，就是论文的格式
1. 第一部分
* [这是文本] [1]
* [这是第二个][2]
\[\]\ \[\]
第一个中括号放内容
第二个中括号放链接重定义
2. 第二部分                              

	 [1]: https://52pojie.cn  "破解论坛"
	 [2]:https://markdown.com.cn "markdown学习web"
格式为 \[\]\: https://examp.com \ "title"
算是一种超链接的方式
另外网址内有空格用 %20 intand space
图片语法 
\!\[图片\] (/local/users/ "magic")
链接图片，一样，建议是使用图床
因为麻烦
## 转义字符
一般使用 \\ 搞定
但 \< 和 \& 有点麻烦
因为在 html 中是需要特殊处理
\< 是起始标签, 使用实体 &lt;
\& 是标记 HTML 实体 , &amp; 
### 特殊知识
 在markdown 中
 &copy; \&是没有变化的，会履行著作权符号
 但如果 AT&T 就会自动转换为 AT&amp;T
 ## HTML
 不在 markdown 语法范围内的标签，则就需要 HTML 来制作
 不需要特别标注 HTML
 
可以直接使用
this **word** is bold, this <em>word</em> is italic
### 区块标签
例如 \<div\> , \<table\>, \<pre\>, \<p\>. 必须在前后加空行，这些元素的开始与结尾标签，不可以使用 space or tab 。避免自动换行
 this is a regular paragraph.
<table>
<tr>
<td>foo</td>
</tr>
</table>

this is another regular paragraph.

另外在 HTML 块级标签内不能使用 markdown 语法
例如 <p> italic and **bold**</p>
不起作用
## 表格
| syntax | description |
|---|---|
| header | title |
|paragraph|text|
这是最基本的，管道分割，三个及以上连字符创建标题
### 对齐
那边对其就在那边添加冒号 :

| syntax | description |
|:---:|:---:|
| header | title |
|paragraph|text|
还能格式化，就是和前面的语法混用
在表中的转移管道字符 ， &#124;

## 脚注
论文的引用
Her's a simple footnote,[^1] and here's a longer one.[^bignote]
[^1]: this is the firs footnote.
[^bignote]: Here's one with multiple paragraphs and code.
     Indent paragraphs to include them in the footnote.
     '{ my code }'
     add as many paragraphs as you like.

## markdown 标题编号
大概是这样
### My Great Heading  {#custom-id}

[Heading IDs] (#heading-ids)

## 定义列表
First Term
:  this is the definition of the first term.

Second Term 
:  this is one definition of the second term.
:  this is another definition of the second erm.

这个处理器不能这样玩
### 删除线
~~理想主义归于平庸~~
前后两个波浪线 就这样 \~\~ 主体 \~\~
### 任务列表
- [ ] 这样子
- [x] 或者这样子
- [ ] 格式是 \- \ \[\ \]，这样是一个空白的
- [ ] \-\  \[x\] ，这样就有对勾了
## 表情符号 
1 :tent: 1
2 :joy: 
obsidian 不支持这玩意儿

## 自动网址
本来是使用方括号
<https://52pojie.cn>
不过直接输入也成
https://52pojie.cn
禁用就
`https://52pojie.cn`





