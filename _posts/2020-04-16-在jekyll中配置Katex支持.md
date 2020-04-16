**在线方式**
1. 在`_includes\head.html`中添加如下代码 
 

>link rel="stylesheet" href="{{ "/static/katex/katex.min.css" | prepend: site.baseurl }}">
><script src="{{ "/static/katex/katex.min.js" | prepend: site.baseurl }}"></script>


1. 在`_layouts\default.html`*</body>*中添加如下内容
~~~`javascript
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
final