---
layout: post
title:  "维基百科保存为MD和打印pdf"
date:   2018-06-09 11:15:51 +0800
categories: markdown
tags: markdown 
description: 维基百科保存为MD和打印pdf.
---
# 维基百科保存为MD和打印pdf

维基百科保存为MD，比较好的方案是采用copytomarkdown CHROME插件。
CopyToMarkdown插件采用reMark.js将HTML转换成Markdown格式，总体来说效果还是挺好的。
但是CopytoMarkdown插件保存维基百科也有几个不如意的地方：

1.维基百科中出现数学公式的地方。维基百科采用Mathjah来显示数学公式，方法和tex的数学公式语法一致。采用CopyToMarkdwon chrome插件，copy出来的数学公式显示成了HTML一大坨，这样在MD格式中预览的时候就是一堆杂乱无章的HTML。

2.维基百科中的代码源程序，采用copytomarkdown chrome插件，也显示成了HTML格式。比如：

```
The traditional ["Hello, world!" program](https://en.wikipedia.org/wiki/%22Hello,_world!%22_program ""Hello, world!" program") can be written in Java as:<sup id="cite_ref-51" class="reference">[[51]](https://en.wikipedia.org/wiki/Java_(programming_language)#cite_note-51)</sup>

<pre>
classHelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello World!"); // Prints the string to the console.
    }
}
</pre>
```
copy成markdown变成

```
## "Hello world" example

The traditional ["Hello, world!" program](https://en.wikipedia.org/wiki/%22Hello,_world!%22_program ""Hello, world!" program") can be written in Java as:<sup id="cite_ref-51" class="reference">[[51]](https://en.wikipedia.org/wiki/Java_(programming_language)#cite_note-51)</sup>

<pre>
classHelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello World!"); // Prints the string to the console.
    }
}
</pre>
```

它是由HTML转换过来的。原来的HTML是下面的样子：

```
<h2><span class="mw-headline" id=".22Hello_world.22_example">"Hello world" example</span></h2>
<p>The traditional <a href="/wiki/%22Hello,_world!%22_program" class="mw-redirect" title="&quot;Hello, world!&quot; program">"Hello, world!" program</a> can be written in Java as:<sup id="cite_ref-51" class="reference"><a href="#cite_note-51">[51]</a></sup></p>
<div class="mw-highlight mw-content-ltr" dir="ltr">
<pre><span class="kd">class</span> <span class="nc">HelloWorldApp</span> <span class="o">{</span>
    <span class="kd">public</span> <span class="kd">static</span> <span class="kt">void</span> <span class="nf">main</span><span class="o">(</span><span class="n">String</span><span class="o">[]</span> <span class="n">args</span><span class="o">)</span> <span class="o">{</span>
        <span class="n">System</span><span class="o">.</span><span class="na">out</span><span class="o">.</span><span class="na">println</span><span class="o">(</span><span class="s">"Hello World!"</span><span class="o">);</span> <span class="c1">// Prints the string to the console.</span>
    <span class="o">}</span>
<span class="o">}</span>
</pre></div>
<p></p>
```


3.乱用黑体。

```
for example, <code>HelloWorldApp.java</code>. 
```

转换成了：
```
for example, `HelloWorldApp.java`. 
```

下面的
```
A <code><b>class</b></code> that is not declared <code><b>public</b></code> 
```
转换成了
```
A `**class**` that is not declared `**public**`
```
在MARKDOWN中渲染不好看。

4.表格。维基百科中有很多表格，在使用copytomarkdown后，有些变成了乱码。

5.图像。维基百科的图像，copytomarkdown后，不能显示。不知道是什么原因。
总体来说，采用copytomarkdown，除了上面几个地方，保存为MD后，还是令人满意的。
