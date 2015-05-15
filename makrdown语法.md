Markdown语法
=============
Markdown主要是作为一种网络内容的写作语言
&lt;div>、&lt;table>、&lt;pre>、&lt;p>等标签必须在前后加上空白以利于与内容的区隔，而这些元素的开始与结尾标签，不可以用tab或是空白来排缩。

举例来说，在Markdown文档中加上一段HTML表格：

	This is a regular paragraph.
	<table>
	<tr>
		<td>Foo</td>
	<tr>
	</table>
	This is another regular paragraph

**请注意**Markdown语法区块中将不会被进行处理
HTML的区段标签如&lt;span>&lt;cite>&lt;del>则不受限制，可以在Markdown的段落、列表或表其里任意使用
HTML 区段标签和区块标签不同，在区段标签的范围内， Markdown 的语法是有效的。
####特殊字符自动转换####
----
在 HTML 文档中，有两个字符需要特殊处理： < 和 & 。 < 符号用于起始标签，& 符号则用于标记 HTML 实体，如果只是想要使用这些符号，必须要使用实体的形式，像是 &lt; 和 &amp;
& 符号其实很让写作网络文档的人很困扰，如果要输入「AT&T」 ，必须要写成「AT&amp;T」 ，还得转换网址内的 & 符号，如果要链接到：

	http://images.google.com/images?num=30&q=larry+bird
必须要把网址转成：

	http://images.google.com/images?num=30&amp;q=larry+bird
	&copy;

Markdown 将不会对这段文字做修改，但是如果这样写：

AT&T

Markdown 就会将它转为：

	AT&amp;T

不过需要注意的是，code 范围内，不论是行内还是区块， < 和 & 两个符号都一定会被转换成 HTML 实体，这项特性让你可以很容易地用 Markdown 写 HTML code （和 HTML 相对而言， HTML 语法中，要把所有的 < 和 & 都转换为 HTML 实体，才能在 HTML 文档里面写出 HTML code。）

####标题####
----
Markdown 支持两种标题的语法，Setext 和 atx 形式
Setext 形式是用底线的形式，利用 = （一级标题）和 - （二级标题），例如：

	This is an H1
	=============

	This is an H2
	-------------
任何数量的 = 和 - 都可以有效果。

Atx 形式则是在行首插入 1 到 6 个 # ，对应到标题 1 到 6 级，例如：

	# This is an H1

	## This is an H2

	###### This is an H6

可以选择性地「关闭」atx 样式的标题，这纯粹只是美观用的，若是觉得这样看起来比较舒适，就可以在行尾加上 #，而行尾的 # 数量也不用和开头一样（行首的井字数量决定标题的级别）：

	# This is an H1 #

	## This is an H2 ##

	### This is an H3 ######
	####Blockquotes####

Markdown 使用 email 形式的区块引言，如果你很熟悉如何在 email 信件中引用，就知道怎么在 Markdown 文档中建立一个区块引言，那会看起来像是强迫断行，然后在每行的最前面加上 > ：

	> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
	> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
	> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
	> 
	> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
	> id sem consectetuer libero luctus adipiscing.

Markdown 也允许只在整个段落的第一行最前面加上 > ：

	> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
	consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
	Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

	> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
	id sem consectetuer libero luctus adipiscing.

区块引言可以有级别（例如：引言内的引言），只要根据级别加上不同数量的 > ：

	> This is the first level of quoting.
	>
	> > This is nested blockquote.
	>
	> Back to the first level.
显示结果为:
> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.

引言的区块内也可以使用其他的 Markdown 语法，包括标题、列表、程序代码区块等：

	> ## This is a header.
	> 
	> 1.   This is the first list item.
	> 2.   This is the second list item.
	> 
	> Here's some example code:
	> 
	>     return shell_exec("echo $input | $markdown_script");

显示结果为：
> ## This is a header.
> 
> 1.   This is the first list item.
> 2.   This is the second list item.
> 
> Here's some example code:
> 
>     return shell_exec("echo $input | $markdown_script");

任何标准的文本编辑器都能简单地建立 email 样式的引言，例如 BBEdit ，可以选择文字后，从菜单中选择增加引言级别。
####列表
---
Markdown 支持有序列表和无序列表。

无序列表使用星号、加号或是减号作为列表标记：

	*   Red
	*   Green
	*   Blue

等同于：

	+   Red
	+   Green
	+   Blue

也等同于：

	-   Red
	-   Green
	-   Blue
显示结果为：

+   Red
+   Green
+  Blue

有序列表则使用数字接着一个英文句点：

	1.  Bird
	2.  McHale
	3.  Parish
很重要的一点是，在列表标记上使用的数字并不会影响输出的 HTML 结果，上面的列表所产生的 HTML 标记为：

	<ol>
	<li>Bird</li>
	<li>McHale</li>
	<li>Parish</li>
	</ol>
显示结果为：

<ol>
<li>Bird</li>
<li>McHale</li>
<li>Parish</li>
</ol>

如果你的列表标记写成：

	1.  Bird
	1.  McHale
	1.  Parish

或甚至是：

	3. Bird
	1. McHale
	8. Parish
显示结果为:

3. Bird
1. McHale
8. Parish

都会得到完全相同的 HTML 输出。重点在于，你可以让 Markdown 文档的列表数字和输出的结果相同，或是懒一点，可以完全不用在意数字的正确性。

列表项目标记通常是放在最左边，但是其实也可以缩排，最多三个空白，项目标记后面则一定要接着至少一个空白或 tab。

要让列表看起来更漂亮，可以把内容用固定的缩排整理好：

	*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
	    Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
	    viverra nec, fringilla in, laoreet vitae, risus.
	*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
	    Suspendisse id sem consectetuer libero luctus adipiscing.

但是如果你很懒，那也不一定需要：

	*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
	Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
	viverra nec, fringilla in, laoreet vitae, risus.
	*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
	Suspendisse id sem consectetuer libero luctus adipiscing.
如果列表项目间用空行分开， Markdown 会把项目的内容在输出时用 <p> 标签包起来，举例来说：

	*   Bird
	*   Magic
会被转换为：

	<ul>
	<li>Bird</li>
	<li>Magic</li>
	</ul>

<ul>
<li>Bird</li>
<li>Magic</li>
</ul>

但是这个：

	*   Bird

	*   Magic

会被转换为：

	<ul>
	<li><p>Bird</p></li>
	<li><p>Magic</p></li>
	</ul>

<ul>
<li><p>Bird</p></li>
<li><p>Magic</p></li>
</ul>
列表项目可以包含多个段落，每个项目下的段落都必须缩排 4 个空白或是一个 tab ：

	1.  This is a list item with two paragraphs. Lorem ipsum dolor
	    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
	    mi posuere lectus.

	    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
	    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
	    sit amet velit.

	2.  Suspendisse id sem consectetuer libero luctus adipiscing.

如果每行都有缩排，看起来会看好很多，当然，再次地，如果你很懒惰，Markdown 也允许：

	*   This is a list item with two paragraphs.

	    This is the second paragraph in the list item. You're
	only required to indent the first line. Lorem ipsum dolor
	sit amet, consectetuer adipiscing elit.

	*   Another item in the same list.
如果要在列表项目内放进引言，那 > 就需要缩排：

	*   A list item with a blockquote:

	    > This is a blockquote
	    > inside a list item.
如果要放程序代码区块的话，该区块就需要缩排两次，也就是 8 个空白或是两个 tab：

	*   A list item with a code block:

        <code goes here>
当然，项目列表很可能会不小心产生，像是下面这样的写法：

	1986. What a great season.

换句话说，也就是在行首出现数字-句点-空白，要避免这样的状况，可以在句点前面加上反斜杠。

	1986\. What a great season.
####程序代码区块
---
和程序相关的写作或是标签语言原始代码通常会有已经排版好的程序代码区块，通常这些区块我们并不希望它以一般段落文档的方式去排版，而是照原来的样子显示，Markdown 会用 <pre> 和 <code> 标签来把程序代码区块包起来。

要在 Markdown 中建立程序代码区块很简单，只要简单地缩排 4 个空白或是 1 个 tab 就可以，例如，下面的输入：

	This is a normal paragraph:

	    This is a code block.

Markdown 会转换成：

	<p>This is a normal paragraph:</p>

	<pre><code>This is a code block.
	</code></pre>

这个每行一级的缩排（4 个空白或是 1 个 tab），都会被移除，例如：

	Here is an example of AppleScript:

 	   tell application "Foo"
 	       beep
 	   end tell
会被转换为：

	<p>Here is an example of AppleScript:</p>

	<pre><code>tell application "Foo"
	    beep
	end tell
	</code></pre>

在程序代码区块里面， &amp;、 &lt; 和 > 会自动转成 HTML 实体，这样的方式让你非常容易使用 

####分隔线
----

你可以在一行中用三个或以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号中间插入空白。下面每种写法都可以建立分隔线：

>		* * *
>		***
>		*****
>		- - -
>		---------------------------------------





####链接####
---

Markdown 支持两种形式的链接语法： 行内和参考两种形式。

不管是哪一种，链接的文字都是用 [方括号] 来标记。

要建立一个行内形式的链接，只要在方块括号后面马上接着括号并插入网址链接即可，如果你还想要加上链接的 title 文字，只要在网址后面，用双引号把 title 文字包起来即可，例如：

	This is [an example](http://example.com/ "Title") inline link.

	[This link](http://example.net/) has no title attribute.
会产生：

	<p>This is <a href="http://example.com/" title="Title">
	an example</a> inline link.</p>

	<p><a href="http://example.net/">This link</a> has no
	title attribute.</p>
如果是要链接到同样主机的资源，可以使用相对路径：

	See my [About](/about/) page for details.   
参考形式的链接使用另外一个方括号接在链接文字的括号后面，而在第二个方括号里面要填入用以辨识链接的标签：

	This is [an example][id] reference-style link.

也可以选择性地在两个方括号中间加上空白：

	This is [an example] [id] reference-style link.
接着，在文档的任意处，可以把这个标签的链接内容定义出来：

[id]: http://example.com/  "Optional Title Here"
Markdown 使用星号（*）和底线（_）作为标记强调字词的符号，被 * 或 _ 包围的字词会被转成用 <em> 标签包围，用两个 * 或 _ 包起来的话，则会被转成 &lt;strong>，例如：

	*single asterisks*

	_single underscores_

	**double asterisks**

	__double underscores__

会转成：

	<em>single asterisks</em>

	<em>single underscores</em>

	<strong>double asterisks</strong>

	<strong>double underscores</strong>

####程序代码
---
如果要标记一小段行内程序代码，可以用反引号把它包起来（`），例如：

	Use the `printf()` function.

会产生：

	<p>Use the <code>printf()</code> function.</p>

结果为：

Use the `printf()` function.

如果要在程序代码区段内插入反引号，可以用多个反引号来开启和结束程序代码区段：

	``There is a literal backtick (`) here.``
