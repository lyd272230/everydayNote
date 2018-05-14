 <meta http-equiv="X-UA-Compatible" content="ie=edge">
1，X-UA-Compatible是神马？
文档：https://www.modern.ie/en-us/performance/how-to-use-x-ua-compatible

X-UA-Compatible是IE8的一个专有<meta>属性，它告诉IE8采用何种IE版本去渲染网页，在html的<head>标签中使用。
可以在微软官方文档获取更多介绍。

为什么要用X-UA-Compatible？

在IE8刚推出的时候，很多网页由于重构的问题，无法适应较高级的浏览器，
所以使用X-UA-Compatible标签强制IE8采用低版本方式渲染。

使用下面这段代码后，开发者无需考虑网页是否兼容IE8浏览器，只要确保网页在IE6、IE7下的表现就可以了。

<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE7" />
//emulate 仿真

给网站添加X-UA-Compatible标签

我建议使用下面的X-UA-Compatible标签：

<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
IE=edge告诉IE使用最新的引擎渲染网页，chrome=1则可以激活Chrome Frame



为了不掩盖重点，直接看
2，问：X-UA-Compatible设为IE=edge是不是等同于不设置？
既然IE=edge是“以最高级别的可用模式显示内容”，那是不是和去掉相同的效果？

答：不一样。
有些因素会自动触发兼容性文档视图，这个时候设置X-UA-Compatible就可以防止这个自动触发的行为。
默认行为大致有这些：
  存在于注册表中的兼容性视图列表，当url匹配时将自动切换到兼容性视图
  在注册表中的对应字段指定了使用兼容性视图来显示所有网站
  未指定DOCTYPE，则使用Quirks模式
  曾经遇到过错误

一个有意思的事实是，设置了<meta http-equiv="X-UA-Compatible" content="IE=edge">之后，
即使未声明doctype，在IE8、IE9（未测试IE10+，不过行为应该类似）下面，页面也不会进入quirks模式。

ref: http://msdn.microsoft.com/zh-cn/library/cc288325


使用 X-UA-Compatible 标头可指定页面支持的 Internet Explorer 版本。
使用 document.documentMode 可确定网页的兼容性模式。


<meta http-equiv="X-UA-Compatible" content="IE=5" />
像是使用了 Windows Internet Explorer 7 的 Quirks 模式，
这与 Windows Internet Explorer 5 显示内容的方式很相似。

<meta http-equiv="X-UA-Compatible" content="IE=7" />
无论页面是否包含 <!DOCTYPE> 指令，均使用 Windows Internet Explorer 7 的标准渲染模式。

<meta http-equiv="X-UA-Compatible" content="IE=8" />
开启 IE8 的标准渲染模式，但由于本身 X-UA-Compatible 文件头仅支持 IE8 以上版本，因此等同于冗余代码。

<meta http-equiv="X-UA-Compatible" content="edge" />
Edge 模式通知 Windows Internet Explorer 以最高级别的可用模式显示内容，这实际上破坏了“锁定”模式。

<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE7" />
EmulateIE7 模式通知 Windows Internet Explorer 使用 <!DOCTYPE> 指令确定如何呈现内容。
标准模式指令以Windows Internet Explorer 7 标准模式显示，而 Quirks 模式指令以 IE5 模式显示。
与 IE7 模式不同，EmulateIE7 模式遵循 <!DOCTYPE> 指令。对于多数网站来说，它是首选的兼容性模式。
在现阶段，IE8 版本推向市场没有多久，份额不高。因此，考虑兼容旧版本的模式值得推荐。

引用：http://zccst.iteye.com/blog/2162187