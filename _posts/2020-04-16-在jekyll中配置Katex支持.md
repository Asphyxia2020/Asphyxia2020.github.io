**注意**，如果是用`githubpage+jekyll`搭建博客,则其markdown的解析引擎为<font color = "red">kramdown</font>。
kramdown和markdown的区别如下：
>
1. 不支持$1_2$这种数学符号
2. #与标题之间必须有空格
3. 换行必须要行尾两个空格
4. 块级元素前面必须要有空行
5. 列表中的引用无法正确显示
6. 列表中的代码块将一个完整的列表分割成了两部分.
7. 在Matrix Zigzag Traversal中, cpp代码中有两个连着的`{`, 结果报错`Liquid syntax error`.
8. 标题中的MD代码为什么不被解析?
9. 如何支持`==highlight==`?
**在线方式**
* 在`_includes\head.html`中添加如下代码  
~~~html
link rel="stylesheet" href="{{ "/static/katex/katex.min.css" | prepend: site.baseurl }}">
<script src="{{ "/static/katex/katex.min.js" | prepend: site.baseurl }}"></script>
~~~  
* 在`_layouts\default.html`*</body>*中添加如下内容  
~~~html
<script>
  $("script[type='math/tex']").replaceWith(function() {
      var tex = $(this).text();
      return katex.renderToString(tex, {displayMode: false});
  });

  $("script[type='math/tex; mode=display']").replaceWith(function() {
      var tex = $(this).html();
      return katex.renderToString(tex.replace(/%.*/g, ''), {displayMode: true});
  });
</script>
~~~   
finally